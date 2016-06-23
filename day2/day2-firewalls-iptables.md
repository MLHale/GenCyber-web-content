# Firewalls

Firewalls are often a first line of defense for an enterprise or home network. In this unit we will understand the fundamentals of firewalls, write firewall rules that configure its behavior and then test if the firewall performs as expected.

## Overview

The name firewall is inspired from its physical manifestation in construction which refers to walls that are designed to stop a fire from spreading.

![Firewall in a substation](https://upload.wikimedia.org/wikipedia/commons/3/3c/Firewall_Electrical_Substation.jpg)

While these firewalls are "cool", we are interesting in a different kind of firewall. The ones that protect internal networks from external networks. These kinds of firewalls allow us to control the flow of information across networks. 

![network firewalls](../img/networkfirewall.png)

All popular operating systems now come with a firewall installed. For server installations we will focus on the NETfilter packet filtering module built into the linux kernel itself. This module acts as a firewall and is configured using the `iptables` command. The command line use of iptables provides the utmost flexibility and control over the firewall configuration.

![iptables screenshot](../img/iptables.png)

### Question

At what [network layer] (https://support.microsoft.com/en-us/kb/103884) does it make the most sense to operate a firewall, considering that it is connecting two different networks?

- [ ] Physical layer  
- [ ] Data link layer  
- [ ] Network layer and above  

Discussion:  
Since the headers on frames are not useful for routing across networks, typically firewalls rules are authored using information starting at the Internet layer and above all the way to the application layer. IP layer firewalls are the simplest and most widely used.

### Firewall as a Collection of Valves

Firewall can be modeled as a collection of valves  

* Each valve/port corresponds to single service  
* Each valve can  
  - Permit traffic in one or both directions  
  - Deny traffic  

![valves](../img/valves.png)  

Here are three basic scenarios to keep in mind.  

First lets consider, **Ports 1 and 4**. These ports are open. Which means they permit packets from internal and external sources. So in the case of TCP protocol, which forms explicit connections or circuits before transmitting data via a handshake mechanism, such connections can be externally or internally initiated.


In the case of **Port 2**, it allows unrestricted flow of information if the connection is initiated internally. However, it blocks all external requests to initiate an information flow. That is, it permits packets from external sources only if they correspond to a “connection” initiated by an internal source. The firewall will not permit connection requests from external sources. This restriction is useful when an internal web client initiates a web browsing request, then the firewall will allow the corresponding incoming response from an external webserver to pass through the firewall. Any connection initiated externally will not be allowed.

Finally, **Port 3** is closed. Which means that it denies all traffic. A closed port may just drop the packets or send back a RST or "Reset" packet. From a security and resource consumption standpoint, it is always better to just drop the packet. Upon denial of access, no additional or useful information should be communicated back.

## Firewall Rules

Firewalls are configured using simple `if then` rules. In a packet filtering firewall, a rule says: `if source, destination and service is a match THEN take this action`. Since there are many rules involved, the order of the rules matters. **A LOT!**

Rules are evaluated in order, starting with the first one at the top until a first match is discovered. If your top rule is very generic then **none of the later specific rules will ever be evaluated**. So it best to start with rules that will most often be required to be invoked and it does not interfere with other rules. 

Always start firewall configuration with a _whitelisting_ philosophy, where you “Deny by default” and then allow only specific information flows. This means, start the firewall configuration by dropping all packets. Then add rules to allow specific traffic patterns as required by our application needs.

Lets look at an example. 

![valves](../img/examplerules.png)  

**Rule 1** permits externally initiated requests to a webserver behind the firewall. So the source is “any” since we cannot anticipate a specific IP address at the time of writing the rule. The destination is the IP address of the webserver and the service specifies the port number where the service is typically hosted. That would be port 80 for a web server. If these three match an incoming packet then the action is “accept”

**Rule 2** permits internally initiated requests out to the Internet. So the source is any ip address in the local network, which we specify as a range of IP addresses but stated here as "localnet". The destination and the service cannot be anticipated at the time of writing the rule so both are specified as “any”. If a packet matches these conditions then the action is "accept". 

**Rule 3** is to deny all other traffic that does not match the previous rules. So all three match conditions are specified as “any” and the action is "reject". 

### Question

What would happen if we re-ordered these rules? Specifically if Rule 3 was exchanged with Rule 1.

Discussion:
Rule 3 is often implemented as a "Default Policy". This policy applies ONLY if a packet matches NONE of the rules specified for the firewall.

## Working with `iptables`

As mentioned before Linux has a firewall built right into the kernel and it is configured using the `iptables` command. Since it is a utility for privileged users, you will need to elevate your privilege level using `sudo` prepended to the `iptables` command everytime. See code block below.This firewall can be set up in several modes like packet filtering, which is the default mode, network address translation, and many others such as mangle, where you can modify the packets as they pass through the firewall. We will focus on the IPv4 packet filtering function here.

To view your current firewall rules, fire off this command in your Linux Server VM. Enter your password if prompted.

```bash
sudo iptables -nL 
```
You should see something like this:
![iptables screenshot](../img/iptables.png)

What are those `-nL` commandline parameters for?  

`-n` This option tell iptables to not resolve domain names for the ip addresses in the matching rules. This results in faster display of the rules.
 
`-L` Lists all the rules in a specified chain. If no chain is specified then all chains are listed.

But wait! what is a **Chain**? A chain is a list of rules that can match a set of packets. There are several built-in chains: INPUT, FORWARD and OUTPUT. For simple usecases INPUT and OUTPUT chains are sufficient. As their names suggest, INPUT chain is a set of rules that match the "incoming" packets to your computer. Similarly, OUTPUT chain is a set of rules that match the "outgoing" packets. As you can see currently both these chains are empty! Also `(policy ACCEPT)` suggests that the default policy for both chains is to accept all packets. So essentially, your firewall is WIDE OPEN at this point. We better start to close it!

> A note before we move forward: When in doubt, consult the iptables manual pages using the following command: `man iptables`. Alternatively, here is the [web version](http://ipset.netfilter.org/iptables.man.html).


Based on a whitelisting philosopy, let's begin by denying all traffic by default.

```bash
sudo iptables -P INPUT DROP 
```
This command uses the `-P` switch to set the default policy for the INPUT chain to DROP. This means drop all incoming packets to your computer. Let's see what the INPUT chain looks like now.

```bash
sudo iptables -nL INPUT
```
You should see something like this. Notice `(policy DROP)`. You should NOT be able to access your server now from your client web-app. Go ahead and try it!
![iptables screenshot](../img/inputdrop.png)

A firewall that does not allow any traffic is not very user friendly or useful. So let's add some rules to the INPUT chain to allow web requests made on the web port, i.e. port 80.

```bash
sudo iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT
```

The command follows this general structure: `iptables <option> <chain> <matching criteria> <target>`   
Let's examine each element in this structure in detail. 

---
`<option>`  Immediately following the iptables command the options components allows to specify the position in which the rule will be inserted into a chain. For example `–A` appends the rule in the specified chain. `–I` inserts the rule at a specified position in the chain starting with 1. 

So this part `-I INPUT 1` says: Insert this Rule at position 1 in the INPUT chain. 

> A few more useful switches: `–D` to delete a rule in a specified position in the chain. `–F` is for flushing the chain, which deletes all rules in a chain. 

---
`<matching criteria>`  
Next comes the MATCH criteria. `-p tcp --dport 80` says: Match all packets with the TCP protocol headed for port 80. Again, port 80 is your default webserver port.


---
`<target>`  

Finally the target component specifies what to do if the matching criteria is met. This component is specified with a `-j` switch which siginifies a jump or go to the specified target chain. So if the packet matches the matching criteria, then the next rule is specified by the value of the target, which can be the name of a user-defined chain or one of the special values that terminate the rule processing. The special terminating values are ACCEPT, DROP, or RETURN.ACCEPT allows the packet in. `-j ACCEPT` above says: Jump to ACCEPT this packet and terminate the rule processing.DROP and REJECT chains, both deny the packet and stop rule processing. But, DROP is safer than REJECT. When REJECT is used, an error packet is sent in response to the matched packet. It is better not to do this to avoid giving any additional information when access is denied.

A non-terminating target chain is the LOG chain. The log chains help to document any anomalies that have been detected in the kernel log. Log prefixes are specified using the following syntax:`--log-prefix prefix`. The prefix can be about 29 characters long.
---

Let's examine the INPUT chain now.

```bash
sudo iptables -nL INPUT
```
![iptables screenshot](../img/inputwebrule.png)

This output looks much similar to the example table that we created earlier. `0.0.0.0\0` is a more detailed description of "any". So the rule is equivalent to saying, match TCP packets from **any** source to **any** desitination on destination port 80. 

If you did it right, your webserver should be accessible again. Go ahead and confirm. 

What about other ports? You would also need port 443 for HTTPS to be open. To do this we need to add another rule. This time let's append it to the INPUT chain using the `-A` option.

```bash
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT
```

Notice that with `-A` you do not have to specify the rule number. The rule just gets added to the bottom of the INPUT chain. Let's look at the INPUT chain now. 

```bash
sudo iptables -nL INPUT
```
![iptables screenshot](../img/inputhttpsrule.png)

The secure web portion of your server should also be now available to client apps. Go ahead and confirm.

There many other advanced firewall rules that can be authored. But these simple rules should be sufficient to demonstrate the inner workings of a Firewall. We have also managed to significantly reduce the exposed ports of the server to those that are absolutely necessary for our application to work. Nothing more.

For more details on iptables, consult these web resources:

[Ubuntu iptables Wiki](https://help.ubuntu.com/community/IptablesHowTo)  
[CentOS iptables Wiki](https://wiki.centos.org/HowTos/Network/IPTables)

### Making Firewall Settings Persistent






## Additional Readings

* [Microsoft The OSI Model's Seven Layers Defined and Functions Explained] (https://support.microsoft.com/en-us/kb/103884)  
* [Ubuntu iptables Wiki](https://help.ubuntu.com/community/IptablesHowTo)  
* [CentOS iptables Wiki](https://wiki.centos.org/HowTos/Network/IPTables)

Copyright 2010-2016 Robin Gandhi All Rights Reserved