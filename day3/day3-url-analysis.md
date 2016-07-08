# Phishing, Mining Information and Social Engineering Tools

## Cybersecurity Commonsense
[Source: DHS Stop. Think. Connect. [Campaign](https://www.stopthinkconnect.org/tips-advice/general-tips-and-advice)]

* __Protect your $$:__ When banking and shopping, check to be sure the site is security enabled. Look for web addresses with `https://` or `shttp://`, which means the site takes extra measures to help secure your information. `http://` is not secure.

* __When in doubt, throw it out:__ Links in emails, social media posts and online advertising are often how cybercriminals try to steal your personal information. Even if you know the source, if something looks suspicious, delete it.

* __Stay current:__ Keep pace with new ways to stay safe online: Check trusted websites for the latest information, and share with friends, family, and colleagues and encourage them to be web wise.

* __Safer for me, more secure for all:__ What you do online has the potential to affect everyone – at home, at work and around the world. Practicing good online habits benefits the global digital community.

## Phishing Humor

Phishing is a play of words on "fishing". The bait is often a email or social media message from a spammer, the fish are the unsuspecting victims who act on them.
> ![dibert1](http://assets.amuniversal.com/c82f58606d5101301d7a001dd8b71c47)

Spammers send out millions of messages, only a few need to succeed...
> ![dibert2](http://assets.amuniversal.com/b0d71fd0abaf01314782005056a9545d)

Phishing victims often fear ridicule and do not report crimes...
> ![dibert3](http://assets.amuniversal.com/b1cbb110abaf01314782005056a9545d)

## Table of Contents
[Introduction](#introduction)  
[Reading a URL](#reading-a-url)  
[URL Tricks](#url-tricks)  
[AntiPhishing Phil Game](#antiphishing-phil-game)   
[Mining Information](#mining-information)  
[Social Engineering Toolkit](#social-engineering-toolkit)  


## Introduction to URLs

Most Phishing attacks start with a specially-crafted URL. A URL is an acronym for Uniform Resource Locator. It is a standard format for locating web resources on the Internet. Most Internet users refer it as the "address for a website". For example, http://www.amazon.com. News story URLs like this one: http://www.cnn.com/2016/07/06/health/juno-jupiter-nasa/index.html are often much longer. On social media sites we are used to seeing short URLs like this one: http://cnn.it/29lG6OK or links on shopping sites: https://amzn.com/0132390779. Even emails are often filled with URLs that senders want us to click on. URLs also give us access to our bank accounts, tax filing, healthcare, billing, and many government services. While we use it everyday, but very few of us are really confident in their abilities to properly read a URL, much less understand what might happen if clicked on. Let's change that.

[Top](#table-of-contents)

## Reading a URL

There are some serious misconceptions about reading a URL. Spammers often take advantage of these when crafting phishing URLs.

> ##### Misconception: Read a URL from Left to Right, just like english [WRONG!]

Consider this email snippet:

```text
Dear user:
Your facebook account has been locked out due to inactivity.
To re-activate your account please on the click below.

	http://activate.facebook.fblogins.net/88adbao798283o8298398?login.asp

```

So is this a facebook URL?  How do we tell if this link is legitimate or not without clicking on it?   
If we just start reading the URL from left to right, like english, then this URL appears legitimate because we encounter the word `facebook` in the URL. But that is not the correct way of reading a URL.

### The "Right" way to read a URL

The Internet is a network of networks. Each network under the control of an authority is a separate **Domain**. For example, organizations like University of Nebraska at Omaha, Facebook or Apple have authority over their own Domains. So URLs which are used to reference computers in a particular network are often called **Domain Names**. Continuing our example, some top-level domains are `unomaha.edu`, `facebook.com` and `apple.com`.

These domain names have to be **unique** on the Internet. So who is responsible for ensuring this? This function is coordinated by ICANN. Here is what is listed on their website: Internet Corporation for Assigned Names and Numbers (ICANN) coordinates the Internet Assigned Numbers Authority (IANA) functions, which are key technical services critical to the continued operations of the Internet's underlying address book, the Domain Name System (DNS).

There is a structured scheme to assign domain names to various organizations. All domain names end in a period `.`. But this period is not always required when using URLs. So it does not matter if it is there or now. Go ahead and paste this URL in your browser window. Notice the period at the end.

```text
www.google.com.
```
The browser still takes you to google.com

The period is the "root" of the entire DNS (Domain Name System). The next level child nodes to this "period" root node are the "com", "edu", "org", "in" names. Next, if the Organization Wikipedia want a domain name like `wikipedia.org`, then IANA or another ICANN-accredited registrar will insert the `wikipedia` node in to the Global DNS system for the Internet. This is where the control of ICANN ends.

Below the `wikipedia` node, the Wikipedia organization has full autonomy and authority to make up whatever names that it wants for specific computers in its **Domain**. So for its Russian office it wants to create a `ru` node, it has full authority to do so.

This is depicted in the figure below.

![domainnames](../img/phishing/domainnames.png)


So if wikipedia wants to name a computer `apple` in its domain, then it has full freedom to do so. The name of the computer on the Internet would be `apple.wikipedia.org.` This URL has nothing to do with `apple.com.` top-level domain.

Now it should be apparent that the "right" way to read a url is to actually start reading it from the *right*. Starting from the right allows us to identify the top-level domain for the URL. There are two simple rules to follow:

* If no single forward-slash character (`/`) exits in the URL, start reading the top-level domain name from the far right to left.

  > For example: https://www.icann.org has no single forward-slash character. It does have a double forward-slash characters (`//`) but that is not what we are looking for. So in this case you start reading the top-level domain from the far right to left. It is `org` and then `icann`

* If single forward-slash(`/`) exists in the URL, then find the farthest one from the right. Then start reading the top-level domain name from that point onwards from right to left.

  > For example: http://activate.facebook.fblogins.net/88adbao798283o8298398?login.asp   
  In this link the farthest single forward-slash(`/`) from the right is between `net` and `88adbao798283o8298398`. So the top-level domain here is `net` and then `fblogins`. Beyond these two names, the organization that owns `fblogins` domain can makeup whaterver names that want, such as `facebook`, `apple` or `google`.   
  So now we know that this link is not affiliated with `facebook` at all!


#### Exercise:

* What are the top-level domain names for these URLs:

  > `http://www.cnn.com/tiger-woods/story.html`  
    `http://www.buy.com.money.ru`

Check your answers with your peers. Do they match?  
[Answer key](./day3/misc.md).

* Which link will you click on? #1 or #2

>1. `ftp://ftp.microsoft.com/software/patches/fixit.exe`
2. `http://www.micosoft.com/software/patches/fixit.exe`

Check your answers with your peers. Do they match?  
[Answer key](./day3/misc.md).


> ##### Misconception: `www` is a standard part of a URL and cannot be changed. [WRONG!]

As we learned above, beyond the top-level domain, the organization that owns the domain has much control over the names of the computers in it. The name `www` was quite commonly give to computers that severed pages to the "World Wide Web". But it is not necessary to name a computer as `www`. For example, it is OK to have names such as `http://www2.nationalgeographic.com` or even `http://web.nationalgeographic.com`

[Top](#table-of-contents)



## URL Tricks


Tricky Links  
http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/phishing.html



[Short URL expander](http://checkshorturl.com/expand.php)  

[Obfuscated Source](http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/obfuscated.html)  

[Encoded IP Addresses](http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/encoding.html)  





```text
216.58.194.36 # One of the IP addresses for google.com

Decimal (Base 10) and Hex (Base 16) Encoding

    First convert to Binary (Base 2)

    216 = 11011000
    58  = 00111010
    194 = 11000010
    36  = 00100100

    Combined Binary   : 11011000001110101100001000100100

    Decimal equivalent: 3627729444     -->    http://3627729444/
    Hex equivalent    : 0xD83AC224     -->    http://0xD83AC224/

Octal Encoding (Base 8)

    Octal equivalent numbers need to be padded with a zero.

    216 = 0330
    58  = 072
    194 = 0302
    36  = 044

    http://330.72.302.44/

ASCII Encoding for www.wellsfargo.com

    Hex Encoding (Starts with % sign)
      www         = %77%77%77

    Decimal Encoding (Starts with &#)
      wellsfargo  = &#119&#101&#108&#108&#115&#102&#97&#114&#103&#111&#46&#99&#111&#109

    Final URL: http://%77%77%77.&#119&#101&#108&#108&#115&#102&#97&#114&#103&#111&#46&#99&#111&#109

    ASCII Table: http://www.asciitable.com/index/asciifull.gif  # This is a useful resource for ASCII conversions

```
[iframe Clickjacking](http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/clickjacking.html)  
[iframe Clickjacking Reveal](http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/clickjacking-reveal.html)  


[Top](#table-of-contents)

## AntiPhishing Phil Game

Link to the Game Site. Demo requires registration :-(  
http://wombatsecurity.com/antiphishingphil

A free training course at OIT.  
https://oit.byuh.edu/help/anti-phishing

Local site licensed copy for Anti-phishing Phil. See shortcut on Lab Desktop.

[Top](#table-of-contents)


## Mining information

[Top](#table-of-contents)

## Social Engineering Toolkit

[Top](#table-of-contents)

#### License
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Cybersecurity Modules</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://faculty.ist.unomaha.edu/rgandhi/" property="cc:attributionName" rel="cc:attributionURL">Robin Gandhi</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
