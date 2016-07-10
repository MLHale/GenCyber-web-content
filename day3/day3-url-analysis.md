# Phishing

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
[Introduction](#introduction-to-urls)  
[Reading a URL](#reading-a-url)  
[URL Tricks](#url-tricks)  
[AntiPhishing Phil Game](#antiphishing-phil-game)   
[Spear Phishing](#spear-phishing)  
[Additional Readings](#additional-readings)

## Introduction to URLs

Most Phishing attacks start with a specially-crafted URL. When clicked on, phishing URLs take you to fake websites, download malware or prompt for credentials.

A URL is an acronym for Uniform Resource Locator. It is a standard format for locating web resources on the Internet. Most Internet users refer it as the "address for a website". For example, http://www.amazon.com. News story URLs like this one: http://www.cnn.com/2016/07/06/health/juno-jupiter-nasa/index.html are often much longer. On social media sites we are used to seeing short URLs like this one: http://cnn.it/29lG6OK or links on shopping sites: https://amzn.com/0132390779. Even emails are often filled with URLs that senders want us to click on. URLs also give us access to our bank accounts, tax filing, healthcare, billing, and many government services. While all Internet users use it everyday, very few are confident in their abilities to read a URL, much less understand what might happen if clicked on. Let's change that.

[Top](#table-of-contents)

## Reading a URL

There are some serious misconceptions about reading a URL. Spammers often take advantage of these when crafting phishing URLs.

> ##### Misconception: Read a URL from left to right, just like English [WRONG!]

Consider this email snippet:

```text
Dear user:
Your facebook account has been locked out due to inactivity.
To re-activate your account please on the click below.

	http://activate.facebook.fblogins.net/88adbao798283o8298398?login.asp

```

So is this a facebook URL?  How do we tell if this link is legitimate or not without clicking on it?  

If we just start reading the URL from left to right, like English, then this URL appears legitimate because we encounter the word `facebook` in the URL. But that is not the correct way of reading a URL.

### The "Right" way to read a URL

The Internet is a network of networks. Each network that is under the control of an authority, is a separate **Domain**. For example, organizations like University of Nebraska at Omaha, Facebook or Apple have authority over their own Domains/Networks that are connected to the Internet. URLs, which are used to reference computers in a particular network are also called **Domain Names**. Continuing our example, some top-level domains are `unomaha.edu`, `facebook.com` and `apple.com`.

These domain names have to be **unique** on the Internet. So who is responsible for ensuring this? This function is coordinated by ICANN. Here is what is listed on the ICANN website:

>Internet Corporation for Assigned Names and Numbers (ICANN) coordinates the Internet Assigned Numbers Authority (IANA) functions, which are key technical services critical to the continued operations of the Internet's underlying address book, the Domain Name System (DNS).

There is a structured scheme to assign domain names to various organizations. All domain names end in a period `.`. But the period is not always required when using URLs. So it does not matter if it is there or not. Go ahead and paste this URL in your browser window. Notice the period at the end.

```text
www.google.com.
```
The browser still takes you to the google search page.

The period is the "root" of the entire DNS (Domain Name System). The next level child nodes are the "com", "edu", "org", "in", etc. Next, if the organization Wikipedia want a domain name like `wikipedia.org`, then IANA or another ICANN-accredited registrar will insert the `wikipedia` node into the Global DNS system for the Internet. This is where the control of ICANN ends.

Below the `wikipedia` node, the Wikipedia organization has full autonomy and authority to make up whatever names that it wants for specific computers in its **Domain**. So for its Russian office, if it wants to create a `ru` node, then Wikipedia has full authority to do so.

This is depicted in the figure below.

![domainnames](../img/phishing/domainnames.png)


So if wikipedia wants to name a computer `apple` in its domain, then it has full freedom to do so. The name of the computer on the Internet would be `apple.wikipedia.org.` This URL has nothing to do with `apple.com.` top-level domain.

Now it should be apparent that the "right" way to read a url is to actually start reading it from the *right*. Starting from the right allows us to identify the top-level domain for the URL. There are two simple rules to follow:

* If no single forward-slash characters (`/`) exits in the URL, start reading the top-level domain names from the far right to left.

  > For example: https://www.icann.org has no single forward-slash characters. It does have double forward-slash characters (`//`), but that is not what we are looking for. So in this case, start reading the top-level domains from the far right to left. It is `org` and then `icann`

* If single forward-slash characters (`/`) exist in the URL, then find the farthest one from the right. Start reading the top-level domain names right to left from that point onwards.

  > For example: `http://activate.facebook.fblogins.net/88adbao798283o8298398?login.asp`   
  In this link the farthest single forward-slash(`/`) from the right is between `net` and `88adbao798283o8298398`. So the top-level domains here are `net` and then `fblogins`. Beyond these two names, the organization that owns `fblogins` domain can makeup whaterver names that it wants, such as `www`, `login`,`facebook`, `apple` or `google`.   
  So now we know that this link is not at all affiliated with `facebook.com`!


#### Exercise:

##### What are the top-level domain names for these URLs:

```
http://www.cnn.com/tiger-woods/story.html   

http://www.buy.com.money.ru
```

Check your answers with your peers. Do they match?  
[Answer key](./misc.md)

##### Which link will you click on? #1 or #2  

```
#1: ftp://ftp.microsoft.com/software/patches/fixit.exe  
#2: http://www.micosoft.com/software/patches/fixit.exe  

```  
Check your answers with your peers. Do they match?  
[Answer key](./misc.md)


> ##### Misconception: `www` is a standard part of a URL and cannot be changed. [WRONG!]

Beyond the top-level domains, a organization or individual that has registered the domain has much control over the names of the computers in their networks. The name `www` is commonly give to computers that serve pages to the _World Wide Web_. But it is not necessary to name a web-server as `www`. For example, it is OK to have names such as `http://www2.nationalgeographic.com` or even `http://web.nationalgeographic.com`. So there is nothing special about the `www` part of a URL.

[Top](#table-of-contents)

## URL Tricks

The knowledge in the previous section should serve you well in reading URLs. But spammers often conceal the real URL in HTML formatted emails or fake websites. Let's explore a few such tricks. Some URL behaviors are browser specific. So for our discussion let's open the links below in a `Chrome` browser.

#### Tricky Links  
http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/phishing.html

##### Link #1  

On the first link, you will notice that it appears to be a legitimate wellsfargo.com URL. But if you hover over the link, your status bar should show `www.google.com`. How did that happen?

![trickyurls](../img/phishing/1-tricky-urls.png)

Examine the page HTML source by right clicking on a blank area of the webpage and selecting `View Page Source` option.

![trickyurls](../img/phishing/2-tricky-urls.png)

![trickyurls](../img/phishing/3-tricky-urls.png)

In the source code you will see that the `href` attribute, which controls the link target is set to `google.com`. This explains the strange behavior. Hovering over links without clicking them will reveal their real destination in the status bar of the browser.

##### Link #2  

For link #2, we explore a peculiarity of browsers. Many browsers will not display, named rightly so, the "shy" character, which is expressed as follows: `&shy`. The page source shows that this character is present in the `href` attribute and the link text. But the character is not displayed in the page!

![trickyurls](../img/phishing/6-tricky-urls.png)

![trickyurls](../img/phishing/5-tricky-urls.png)

Chrome shows the `&shy` character in the status bar. Some other programs/browsers may not display it at all. Spammers can register domains with `&shy` characters to manipulate users into clicking the links.

##### Link #3  

Link #3 is straight-forward, but a bad practice. Legitimate emails often use this technique, but it conceals the true link and conditions users to click on such links. When sending out emails, avoid such practices.

##### Link #4

Link #4 is very strange looking. You may examine the page source and still have no additional clues. Naively following the two rules of reading a URL from above, you may end up thinking that this is a `wellfargo.com` URL. But it is not!

![trickyurls](../img/phishing/7-tricky-urls.png)

If you hover over the link in Chrome, much to our surprise it turns out to be `google.com`!!!!

![trickyurls](../img/phishing/8-tricky-urls.png)

This URL uses two methods to trick users.
* Hex encode the URL letters. The full conversion table is available here: http://www.asciitable.com/index/asciifull.gif Using this table we can decode the letters as follows:
```
%67 = g
%6F = o
%6F = o
%67 = g
%6C = l
%65 = e
%2E = .
%63 = c
%6F = o
%6D = m
```
So the last part of Link #4 is `google.com`

* This URL also uses an arcane URL technique to specify the login and password as part of the link itself. Some insecure websites allow login requests in the following manner.   

	```text
	http://username:password@example.com

	For link #4:
	username = wellsfargo.com
	password = login
	website  = google.com

	http://wellfargo.com:login@google.com

	Tricky indeed!
	```

With these tricks uncovered, the previous two URL reading rules will suffice now to know what the true top-level domains are. Certainly not `wellsfargo.com`.

##### Link #5

The next link is very mysterious as well. By hovering over it or examining the page source, you will notice that it is a **short URL**. A short URL is notoriously deceptive as you cannot tell where it will take you once clicked on.

To overcome this issue, we will use a service that expands the short URL and provides a preview of the final destination.

**Short URL expander**: http://checkshorturl.com/expand.php

Upon using the URL expander service, it is apparent that this short URL redirects to `google.com`.

![trickyurls](../img/phishing/9-tricky-urls.png)

##### Link #6

At first glance, Link #6 is a short URL too. Let's just copy this link from the browser and check it using the URL expander service. You will determine that it is `google.com`.

But, now hover over the link or view the page source to examine the real link in the `href` attribute. It appears to be a slightly different short URL!

![trickyurls](../img/phishing/10-tricky-urls.png)

If you expand this different short URL, it leads you to `duckduckgo.com`.

Spammers may trick you by making such subtle modifications in the HTML page.

##### Link #7

Hover over link #7 to examine its real destination. What happens?

Using JavaScript, the page automatically redirects you to `google.com` when your mouse hovers over the link! The script is triggered by a `onMouseOver` event.

When visiting questionable websites, it is prudent to turn off JavaScript or use JavaScript blocking extensions such as [No-Script](https://noscript.net) or [ScriptSafe](https://chrome.google.com/webstore/detail/scriptsafe/oiigbmnaadbkfbmpbfijlflahbdbdgdf?hl=en)

#### Obfuscated Source

Examine this new link now:
http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/obfuscated.html

It is identical to the previous page in form and function, but examine its page source.

Most links on this page have been obfuscated. Spammers do this to avoid detection and analysis. Navigate away from such pages or delete emails that have gone to such lengths to conceal their "trickeries".

The `HTML` column in this encoding table: http://www.asciitable.com/index/asciifull.gif explains how the obfuscation on this page works. For example, `&#119;` maps to the letter `w`. A browser does this automatically and renders a human readable webpage.

#### Encoded IP Addresses

Examine links on this page: http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/encoding.html  
Have you seen links like this before? Examine the page source. Finally, click on them to reveal their true destinations.

Most humanly readable domain names map to IPv4 addresses. IPv4 addresses are 32 bit binary numbers. Typically, they are expressed as 4 sets of decimal numbers from 0-255. For example, `unomaha.edu` maps to 137.48.1.231 IP address.

It just so happens that 32 bit IP addresses can be expressed in Octal, Decimal and Hex formats. Browsers know how to interpret IP addresses in these formats.

##### Link #1-3

Links #1-3 are explained below for an IP address that maps to `google.com`

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

    Octal equivalent numbers need to be padded with a leading zero.

    216 = 0330
    58  = 072
    194 = 0302
    36  = 044

    Octal equivalent: http://0330.072.0302.044/
```

> **Security Tip**: Never visit links that have IP addresses or numbers as their web address. These are most likely machines connected to the Internet with no legitimate Domain Name mapping. Anybody can set them up.

##### Link #4

As we saw before, URLs embedded in HTML pages can be encoded in Hex or Decimal encodings. Link #4 `href` generation is explained below.

```text
ASCII Encoding for www.wellsfargo.com

    Hex Encoding (Starts with % sign)
      www         = %77%77%77

    Decimal Encoding (Starts with &#)
      wellsfargo  = &#119&#101&#108&#108&#115&#102&#97&#114&#103&#111&#46&#99&#111&#109

    Final URL: http://%77%77%77.&#119&#101&#108&#108&#115&#102&#97&#114&#103&#111&#46&#99&#111&#109

		This forms the href attribute of Link #5.

    ASCII Table: http://www.asciitable.com/index/asciifull.gif
		# This is a useful resource for ASCII to hex, decimalconversions

```

##### Link #5

Link #5 is a image map. Different regions of the image are mapped to different URLs. Try hovering your mouse over the image starting from the far right, slowly moving towards the left. Notice the change in links in the status bar. Spammers trick victims by embedding images with a mix of malicious and legitimate links using this technique. For example, by chance you may hover over a image area with legitimate links when checking the status bar, but then click a different (malicious link) area to visit the linked website.

#### Highjacking Clicks

Visit this link.
http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/clickjacking.html

At first, there is nothing unusual about this page. There is just a single link to "like the kitten".

As you should know very well by now, nothing is as it seems. To reveal the true nature of this page click on a modified version of this page below.
http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/clickjacking-reveal.html

![trickyurls](../img/phishing/clickjacking-reveal.png)

Now you can see, that the page is crafted to steal your _clicks_ and pass them on to an invisible page in front of it. Spammers do this to generate advertisement revenue from unsuspecting users by _stealing_ their clicks. This exploit is called **click jacking**. You may explore the page source on these pages to notice that such behavior is possible using html `iframe` technology. With an invisible `iframe` the entire page becomes a minefield for your mouse clicks!

In the demo page, `Like the kitten` is strategically placed on a link that tweets great things about Dr. Gandhi. You would be "liking" me without really intending to do so!

![trickyurls](../img/phishing/clickjacking-tweet.png)

When playing "free" online games, you may be clicking invisible advertisements! Don't worry the game in the next section is safe :-)

[Top](#table-of-contents)

## AntiPhishing Phil Game

Let's play a game to test your URL "Know-How". The game is called AntiPhishing Phil.

Here is a link to the game site. Registration is required to play the demo game :-(  
http://wombatsecurity.com/antiphishingphil

A free training course is available at OIT. This is free to play:  
https://oit.byuh.edu/help/anti-phishing

For a local site licensed copy for Anti-phishing Phil, see shortcut on Lab Desktop.

[Top](#table-of-contents)

## Spear-Phishing

Crafting URLs is just one part of the deception used by Spammers. *Spear-Phishing* is a social engineering technique where a spammer uses intimate details about your life, your contacts and recent activities to tailor a very specific attack.

Watch this 3 min video (if you do not have audio, it is OK):   
https://www.youtube.com/watch?v=F7pYHN9iC9I

There is a ton of information on the web pertaining to most of us. This is true even if you do not use social media. Voting registries, court records, county and property records, phone books, online review sites are just some examples. If you use social media, then there is a lot more information to collect. All you need is a Name to start your reconnaissance.

Visit these sites and see how much information is available about yourself:   
`www.pipl.com` and `www.spokeo.com`

You may have to pick out yourself from other people who share your name. But that should be easy with additional information about your age and location.

Sites like Facebook, Linkedin, Company websites, Organizational Charts and Employee directories, make it easy to craft emails from colleagues, friends and family. There are commercial tools available to collect what is called Open Source Intelligence or (OSINT). Here is a tool that does just that: https://www.paterva.com/web7/buy/maltego-clients/maltego.php


> **Security Tip**: Even when clicking on links in emails or websites shared by close colleagues, friends and family; trust but verify.

[@Matt: Add the twitter mashup with geolocation that you shared with me]

[Top](#table-of-contents)

## Additional Readings

* Infographic, Phishing: [How many take the bait?](http://www.getcybersafe.gc.ca/cnt/rsrcs/nfgrphcs/nfgrphcs-2012-10-11-en.aspx)
* [Reporting Phishing](https://www.consumer.ftc.gov/articles/0003-phishing), Federal Trade Commission
* APWG, Phishing [Public Education](http://phish-education.apwg.org/r/en/index.htm)

[Top](#table-of-contents)


#### License
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Cybersecurity Modules</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://faculty.ist.unomaha.edu/rgandhi/" property="cc:attributionName" rel="cc:attributionURL">Robin Gandhi</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
