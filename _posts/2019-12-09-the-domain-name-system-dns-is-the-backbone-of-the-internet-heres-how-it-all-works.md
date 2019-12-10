---
title: The Domain Name System (DNS) is the backbone of the internet. Here’s how it
  all works.
image: "/assets/default-social-image.png"
categories: DNS
---

The Domain Name System (DNS) is often called as the backbone of the web network. Several engineers and their associations are operating it, eventually shaping the internet's status in the future.

I remember attending a great week of round table talks on the scope of the internet world and it's future, which included:

* DNS Policy Development Seminars
* Workshops on how the internet architecture works
* Where the Internet is most vulnerable and insecure

It's been a great experience, and I got quite a lot of interest from it

I'm fairly new to the domain world as well as the internet architecture's inner workings, just going back a little. As a developer with iwantmyname, I had to learn a shitload since entering this space. There is a huge maze underneath the surface of the browser. Therefore I crafted this tutorial to take you through some of the technology behind the domain names and numbers that we all use every day.

**How does the internet work?**

“This is a very common interview question: what happens when you go to Google.com, enter a query, and press enter?”
— [Quincy Larson](https://www.freecodecamp.org/news/the-domain-name-system-dns-is-the-backbone-of-the-internet-heres-how-it-all-works-5706d0afa0fa/undefined)

Now you launch your browser and go to freecodecamp.com, and this amazing page becomes loaded in the blink of an eye right in front of you. You may realize this page is made from a collection of compressed files somewhere sitting on a database. But how does your computer in the infinitely expanding web make its way to such archives? You may begin to think...

**What happened?**

Your browser didn't really know what the IP address of freecodecamp.com is, the very first time you travel to freecodecamp.com, so it couldn't link and access certain data. Neither, for that instance, did it know where those data are being held on the physical servers. And hence, from where to grab such data to begin building the website, it had no indication.

So what happens: (cue the graphics!)

[DNS Chat](https://imgur.com/a/xj0fP)

**Okay, let me spread that a little bit**

* A user requests to visit freecodecamp.com to their browser
* The browser queries a "where is freecodecamp.com" DNS Resolver (usually their ISP)?
* "Where is. COM?" DNS Resolver asks the Root servers (that have a big list that holds this info) "where is. COM?" Responds to Verisign.
* Instead DNS Resolver tells Verisign — "Where is freecodecamp.com?" Verisign responds to ns1.cloudflare.com and 192.168.178.1 IP address.
* The IP address of hosting servers is queried. "Show me the 192.168.178.1 (please) IP address files"
* On the page, database files are supplied and made so that users can learn to code ... or whatever they did.

I captured this [Verisign](https://www.verisign.com/en_US/website-presence/online/how-dns-works/index.xhtml) screencast, which is by far the world's largest .com, .net, .cc, .tv and .name register. It displays you the mechanism in a good way as the protocol operates through the DNS structure through the sequential queries and replies.

Do not really think too hard too much about attempting to read all of the text, but rather just watch the exchanges and information flow to restate what we've spoken about here (it was on a loop so it's going to restart).

[DNS Chat](https://imgur.com/a/MnXeU)

**Who makes it work?**

In short IANA, in long ICANN, (in a moment I'm going to explain these organizations and all this will make more sense)

The reason why something works was to find out who makes it work — the main question and purpose for this article. Thinking things are just working, is easy. Yet, of course, it's no mistake, due to the current protocols and policies that have been developed and achieved enough acceptance to become universal conventions, the way the internet works is, but then who decides on these and how?

In simple terms, this function falls within the competence of IANA (Internet Assigned Numbers Authority) with particular reference in how domain names and IP addresses are mapped. They have the mandate to ensure that the proper technical procedures are in place to have a secure and stable domain name system. That takes us to ICANN (Internet Corporation for Assigned Names and Numbers). For ICANN, there is no analysis of IANA:

Besides providing technical operations of vital DNS resources, ICANN also defines policies for how the “names and numbers” of the Internet should run. The work moves forward in a style we describe as the “bottom-up, consensus-driven, multi-stakeholder model” — ICANN.COM

In September 2015, the IANA function run by ICANN since 1998, forever moved from a contract with the U.S. Department of Commerce to ICANN's autonomous control, and has a board members and also as a body, is split into distinct member organizations, let's examine the multi-stakeholder system:

“ICANN’s inclusive approach treats the public sector, the private sector, and technical experts as peers. In the ICANN community, you’ll find registries, registrars, Internet Service Providers (ISPs), intellectual property advocates, commercial and business interests, non-commercial and non-profit interests, representation from more than 100 governments, and a global array of individual Internet users. All points of view receive consideration on their own merits. ICANN’s fundamental belief is that all users of the Internet deserve a say in how it is run.” — ICANN.COM

Although it is fair to say that all of these communities are "represented," I will assert that not all of them are equally represented. It's natural to assume those who have more financial interest and spending money to try to pull the discussion into a certain path. AT&T, Comcast, Charter, Verizon, Vodafone, T-Mobile, Orange, as example for the telecom industry.

They may drag us backwards in which they can package up websites like they did with cable television channels and distribute them to end users, financial burden of the traffic on the cables they control, and typically triple-dip on a closed internet and they can create yet more revenue.

Many governments will also attempt to influence their own state interests in a way, whereas others will attempt to become more global citizens. Intellectual Property activists (associations that generally consist of IP attorneys) need it to be much more of IP and brand security so they can preserve their high paying customers valuable assets.

Service providers in the commercial industry, such as Facebook and Google, are prominent in the spectrum which seek to campaign — at least to some extent — for the confidentiality of their customers to preserve their own internet dominance.

Registries such as Verisign are interested in developing beneficial policy outcomes that they are bound to fulfill.



Curiously, in my knowledge, it is the Registrars— with which you can register domains (such as iwantmyname) — who provide the fray with a voice of reason. They have to weigh their ICANN and Registries commitments against their customers obligations. And as a result, they often need to fight back toward different members or interest groups, or even the ICANN committee itself at times.

**Let’s talk end users**

Hey! That’s us!

In this phase, there is a significant lack of end-user engagement. If the end internet users were paying closer attention, we all would be better off.

Note that there are some 4 billion internet users, and only a few individuals are holders of stakes in telecoms, registers or web platforms. There are millions of members in the freeCodeCamp network alone, but together we share so much that is at stakes.

That said, there are a very small number of people currently engaged in this discussion— maybe just a few thousand. To really be truthful, I believe that there is an increasing need for further programmers well into the debate to take a much more active voice.

After all, this is our livelihood. It's where our time wants to be consumed. It is the space which absorbs a great deal of our focus, energy, and passion. And besides being highly competent and heavier internet users, we also have valuable insights in our own communities. We could speak with a compassionate voice with an even greater end-user base.

**What can you do?**

At the table (or on the carpet) you should take a seat. You can get active in a few forms, based on how structured you like the participation to be. You may enter [At-Large](https://atlarge.icann.org/).

[At-Large](https://atlarge.icann.org/) is representative of the multi-stakeholder system for ICANN's end-user community. It is divided into At-large outreach groups (RALOs). NARALO (North America), EURALO (Europe), APRALO (Asia-Pacific), LACRALO (Latin American and Caribbean Islands) and AFRALO (African Nations).

Such different RALOs feed their inputs into the At-Large Advisory Committee (ALAC) which is reporting to ICANN in exchange.

There are other organisations within these collective groups of end-users that you can become member of at university or city level.

An other way to get engaged is to be a non-affiliated participant, i.e. outside an At-Large structure, and effectively with your Regional At-Large group. (Note that currently only the RALOs from North America, Europe and Asia Pacific allow such members— [find out more and apply here](https://atlarge.icann.org/get-involved/individual-member).)

There's another method, and that's by submitting to become an [ALS](https://atlarge.icann.org/alses) as a community. On your side, it requires some effort. You'd need to assemble and lead your group's individuals. However the pay-off is a table seat and a [voice for those represented by your ALS](https://atlarge.icann.org/get-involved/about-als).

I would like to know your feedback on a sidenote about whether you believe that the freeCodeCamp group itself should look into implementing to be an At-Large Structure. It would give all supporters of it a path into ICANN's end-user group.

There's another way you can participate outside of the At-Large structure. You can weigh at those once ICANN decides to open topics for public consultation. [Here's where they can be found](https://www.icann.org/public-comments).

You may also join like I did in an ICANN conference. ICANN plans to hold in a different part of the world three times a year.

Attending one of these one-week conferences is quite a worthwhile experience. They are free and open to the public. All you need to do is register and apply. They also [provide fellowships](https://www.icann.org/fellowshipprogram) to assist you if you need some help to do so.

You could express your views and help shape the future of our free and open internet in many ways.

“All users of the Internet deserve a say in how it is run.”
— ICANN

So I'm encouraging you to get involved and take a seat at the table.

$USER We made it \o/ that was a lot to take in and process
Response: You humans with your little CPU, LOL :)