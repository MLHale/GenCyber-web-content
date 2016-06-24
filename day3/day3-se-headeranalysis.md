# Email Header Analysis

## Introduction

Email is an indispensable communication tool. We use it everyday. Unfortunately many attacks also originate in emails. Wouldn't it be great if everyone had some email super ninja skills!

It may come as a surprise that spoofing email addresses is the easiest thing a hacker can do! Turns out it is also most effective. Take a look at some of the statistics in the [Verizon Data Breach Reports](http://www.verizonenterprise.com/verizon-insights-lab/dbir/).

Here is an interesting one:

> How long does an attacker have to wait to get that foot in the door? We aggregated the results of over 150,000 e-mails sent as part of sanctioned tests by two of our security awareness partners and measured how much time had passed from when the message was sent to when the recipient opened it, and if they were influenced to click or provide data (where the real damage is done). The data showed that nearly 50% of users open e-mails and click on phishing links within the first hour. [Verizon DBIR 2014]
> ![verzon dbir stats](../img/email/dbirstats.png) 

If you are a bad guy, that is the easiest way for getting malware into an organization. So it is prudent to understand exactly where an email is “really” coming from before opening or clicking on it. By the end of this unit you be able to do just that.

## Email Headers

Email Headers hold a lot of information. In fact they have so much information that they are never displayed entirely to the user! The email reader only sees a few pieces of information out of this header. 

Before we get started, I would like to share my own personal accomplishment. A email from President Barack Obama.







