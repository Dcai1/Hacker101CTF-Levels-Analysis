# Introduction

Being part of Cyber Security is a daunting task; ranging from tasks such as writing intelligence reports, securing network infrastructure and security, 

### but most importantly, ensuring sensitive information does not **fall into the wrong hands**.
<br />

But that also raises the question, **how does information fall into the wrong hands in the first place?** <br />

So to fix this gap, I dive into the depths of an attacker using Hacker101's **CTF** _(Capture The Flag)_ **gamemode**, learning their tactics and even forming some techniques of my own. <br />

With my previous **background experience** specializing in **Web Development**, this gives me an edge over many other testers since I have first-hand experience developing and implementing features into web applications, so I understand how they all work behind the scenes.

Let's get into it!

##### Also, you can't set up defenses as Cyber Security if you don't even know what the attacks are! 

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

I'm going to skip ahead to the second level, since the first level is such a tutorial, it makes me fall asleep.
<hr />

<br /> <br />

## Micro CMS v1 - Easy

**Takeaway:** Relatively **simple**. It lacked authorization checks, which as a consequence, allowed all users to act as if they were an admin, because there was nothing authorizing user actions!

<hr />

**Summary**:
* Post ID Manipulation
* No Sanitization (XSS, SQLi)
* SQL Injection

<hr />


**No** penetration tools were needed for this. Simply **navigating** around the web application to understand how it works was enough to analyze and locate vulnerabilities to exploit it in unintended ways. (*or in this context, intended!*)

<hr />

### My Approach, Summarized

After collecting information on the website, I noticed most components were **rich-text fields**, and no general **authentication** and **authorization** on the application. After deploying thorough **testing**, it was obvious input fields were not sanitized, opening up approaches for **XSS**, **SQLi**, and **unauthorized** **CRUD** operations on existing posts.


Anyway, not much to learn here. Let's move onto the next one, which is conveniently called:

<br />

## Postbook - Easy

**Takeaway:** **Don't use guessable, numeric IDs.** <br /> Blog-like application that had everything but authorization and standard ID labelling. Teaches many of the **techniques**, **tactics**, and **procedures** that attackers will take in exploiting a web application, ranging from **numeric** post ID interactions, to techniques like **brute-forcing** and **cookie manipulation**. <br />

<hr />

**Summary**:
* Post ID Manipulation (again)
* Post ID Navigation
* Password Brute Forcing
* Inspect/Dev Tools Usage
* API Manipulation
* Session Cookie Manipulation

<hr />

I used a couple of penetration tools for this, mainly **Burp Suite** for intercepting internet traffic, and extensions that allow cookie editing.

<hr />

### My Approach, Summarized

This website gives me a blog-like feeling, with the posts, CRUD operations using API routes, and authentication. Though, not much for authorization. <br /> To summarize, this blog application has: <br />

1. User Accounts + Authentication
2. Numeric Post IDs
3. API Routes
5. Session Cookies
6. No Authorization

There are already two user accounts on the website: "**admin**" and "**user**". I brute-forced the password of both accounts, with only the latter proving successful (extremely weak password). This is why strong passwords should be **reinforced** using a **ReGex** check during account creation. <br /> <br /> 

As a result, I signed in as **user** and gained access to all the current posts, including permissions of everything a regular user can do. <br />

I tested the post `edit` and `delete` API routes. **No authorization**. <br />

I combined this flaw with the existing numeric post IDs. **No authorization**, could edit and delete posts of **other** users. <br />

Lastly, I viewed the session cookie and realized it was **hashed** with **MD5** because it was exactly **32 characters long**. I would **brute-force** the hash, but settled with educated guesses since all IDs so far were **numeric**. **It worked.** Just like posts, the cookie was just a numeric number hashed with MD5. I manipulated the values to sign in as the **admin** account. That was enough to end this challenge.

<br />
<br />

Use unique UUIDs for post and account IDs. Hash them using stronger algorithms like SHA-512 and salting.


<br />

## Micro-CMS v2 - Medium

**Takeaway:** This is where levels start applying some form of resistance, which is what I really liked! There can't be a challenge if there isn't any resistance at all. The web application from Micro-CMS v1 applied patches to the vulnerabilities known from the last, patching everything except for **SQLi**.

<hr />

**Summary**:
* SQL Injection
* Database Dumping
* Unauthorized API remote communication (curl)

<hr />

Penetration tools were used for this, mainly **Burp Suite** and **SQLMap** from Kali Linux.

<hr />

### My Approach, Summarized

They added **authentication and authorization**. Post **creation** and **editing** is now exclusive to admins. We can only **read** posts. <br />

After some analysis and navigation through the web application, I noticed a new **login** page, with no option to create an account. This page was home to the classic two inputs, **username** and **password**. <br />
After calculated testing, it was sanitized against XSS, but **not** SQLi.

Using **SQLMap** from Kali Linux to **dump** the database by providing the username and password parameters, I extracted the **database** **table** **names** and all data inside of them, **including** the admin login credentials. <br />
With this information, everything afterwards became relatively **simple**.

<br />



