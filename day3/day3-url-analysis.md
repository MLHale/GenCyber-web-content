# URL Analysis

## Cybersecurity Commonsense
[Source: DHS Stop. Think. Connect. [Campaign](https://www.stopthinkconnect.org/tips-advice/general-tips-and-advice)]

* __Protect your $$:__ When banking and shopping, check to be sure the site is security enabled. Look for web addresses with `https://` or `shttp://`, which means the site takes extra measures to help secure your information. `http://` is not secure.

* __When in doubt, throw it out:__ Links in emails, social media posts and online advertising are often how cybercriminals try to steal your personal information. Even if you know the source, if something looks suspicious, delete it.

* __Stay current:__ Keep pace with new ways to stay safe online: Check trusted websites for the latest information, and share with friends, family, and colleagues and encourage them to be web wise.

* __Safer for me, more secure for all:__ What you do online has the potential to affect everyone – at home, at work and around the world. Practicing good online habits benefits the global digital community.


## Table of Contents
[Introduction](#introduction)  
[Reading a URL](#reading-a-url)  
[URL Tricks](#url-tricks)  
[AntiPhishing Phil Game](#antiphishing-phil-game)  


## Introduction

A URL is an acronym for Uniform Resource Locator. It is a standard format for locating web resources on the Internet. Most Internet users refer it as the address for a website. For example, http://www.amazon.com. We also often share much longer URLs, such as a news story like this one: http://www.cnn.com/2016/07/06/health/juno-jupiter-nasa/index.html. On social media sites we are used to seeing short URLs like this one: http://cnn.it/29lG6OK or links on shopping sites: https://amzn.com/0132390779. Even emails are often filled with URLs that senders want us to click on. URLs also give us access to our bank accounts, tax filing, healthcare, billing, and many government services. While we use it everyday, very few of us are really confident in their abilities to properly read a URL, much less where it might take them if clicked on. Let's change that.

[Top](#table-of-contents)

## Reading a URL

There are many common misconceptions about reading a URL.

#### Misconception 1: Read a URL from Left to Right, just like english.



#### Misconception 2: `www` is a standard part of a URL and cannot be changed.



#### Misconception 3: All parts of the URL before the domain name need to be registered.



[Top](#table-of-contents)

## URL Tricks

[Tricky Links](http://faculty.ist.unomaha.edu/rgandhi/phishing-demo/phishing.html)  
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

#### License
<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Cybersecurity Modules</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://faculty.ist.unomaha.edu/rgandhi/" property="cc:attributionName" rel="cc:attributionURL">Robin Gandhi</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
