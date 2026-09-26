# Introduction

Being part of Cybersecurity is a daunting task; ranging from tasks such as writing periodic intelligence reports, securing network infrastructure and security, 

### but most importantly, ensuring sensitive information does not **fall into the wrong hands**.
<br />

But that also raises the question, **how does information fall into the wrong hands in the first place?** <br />

So to fix this gap, I dive into the depths of an attacker using Hacker101's **CTF** _(Capture The Flag)_ **gamemode**, learning their tactics and even forming some techniques of my own. <br />

With my previous background specializing in Web Development, this gives me an edge over many other testers since I've have first-hand experience developing web applications and understand how they all work behind the scenes.

Let's get into it!

##### Also, you can't set up defenses as Cybersecurity if you don't even know what the attacks are! 

# Levels Overview

<br />

There are levels ranging from various difficulties, those being **Easy, Medium, and Hard!**. In particular, I focused on Medium challenges and higher, so the defenses became more and more realistic to the security of an actual application.

# Levels Completed
##### from Easy - Hard
<hr />
<ol>
<li><b> A little something to get you started -</b>  Easier than Easy </li>
<li><b> Micro-CMS v1 </b> - Easy </li>
<li><b> Postbook - </b> Easy </li>
<li><b> Micro-CMS v2 </b> - Medium </li>
<li><b> Cody's First Blog </b> - Medium </li>
</ol>

I'm going to skip ahead to the second level, since the first level is such a tutorial in that it makes me fall asleep.
<hr />

<br /> <br />

## Micro CMS v1

**Takeaway:** This one was relatively **simple**. It lacked authorization checks, which as a consequence, allowed all users to act as if they were an admin, because there was nothing authorizing user actions!

**Summary**:
* Post ID Manipulation
* No Sanitization (XSS, SQLi)
* SQL Injection


No penetration tools were needed for this. Simply navigating around the web application to understand how it works was enough to analyze and locate vulnerabilities to exploit it in unintended ways. (or in this context, intended!)

Anyway, not much to learn here. Let's move onto the next one, which is conveniently called:

<br />

## Postbook

**Takeaway:** This next **easy** difficulty level shows all the many techniques and procedures that attackers may take in invading a web application, ranging from simple inspect element interactions, to techniques like **cookie manipulation**.  <br />
All in all, this is a **great** level for getting familiar with the basics of every technique an attacker may use against our applications.

**Summary**:
* Post ID Manipulation (again)
* Brute forcing
* Inspect/Dev Tools Usage
* API Manipulation
* Session Manipulation

I used a couple of penetration tools for this, mainly Burp Suite for intercepting internet traffic, and Kali Linux.

TODO: add more


