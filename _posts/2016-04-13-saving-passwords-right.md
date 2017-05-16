---
layout: post
title : Saving passwords in database
categories : [Tech]
---

We have all been victimns of one massive database hijack or the other and if your answer to the previous rhetoric was a no, headout for a quick safety-check for these major data breaches that happened at [Adobe][adobe-hack], [Linkedin](linkedin-hack), [eHarmony](eHarmony-hack) and so it goes.

Given the current state of attacks, the logical and sound approach while designing your database - more importantly about how you handle the storage of user passwords, should be in such a way that it reveals no information about a user's actual password. Especially since password reuse is a very common issue.

{% icon fa-quote-left %} [Anything that can go wrong, will go wrong.][murphys-law] {% icon fa-quote-right %}

I will go over a bunch of ways - with increasing level of safety, to saving passwords in your database. A fair warning to those who are new to the security domain : while these methods offer an increasing level of "protection", it is strongly recommended to use the safest one. The order is just to give you a glimpse of the evolution.


0. Plain Text Passwords
---------------------------
Saving user passwords in plain text. This is mostly done by the sites that can email you your password. Seriously, stay away from them. In the event of a data breach, you would handing over all your passwords to the attacker in plain text. And since most people reuse passwords, you are also handing over the key to access a bunch of other services of your users - potentially bank passwords included! Unless you hate your users with all your heart, ==do not do this==


1. One way Hash functions
--------------------------
This is basically the user's password passed to a one-way function. The basic idea of a hash function is that you get the same output as long as your input remains constant. One-way function implies that, given only the output, you can never reconstruct the input. A quick example : MD5 hash of the plain text "password" is "5f4dcc3b5aa765d61d8327deb882cf99". It's actually quite simply to use this method. Most languages have built-in support to generate hash values for a given input. Some commmon hash functions you could use are MD5 (weak), SHA1 (weak) or SHA-256 (good). Instead of saving passwords, just save SHA256(plain-password) and you would be doing the world a favor by not being stupid!


2. Hash + Salt
-------------------------
Now imagine an attacker with a big list of commonly used passwords and their MD5 hash - it's actually very easy to get [such a list][common-passwords]. If such an attacker gets hold of your database, all your users with trivial passwords will be exposed - yes, it's too bad the user used a weak password but nevertheless, we wouldn't want the attackers to find out that someone is using a trivial password! The good news is that MD5 or any good hash function, changes significantly even for a slightest change of input.

```
md5(password) = 5f4dcc3b5aa765d61d8327deb882cf99
md5(password1) = 7c6a180b36896a0a8c02787eeafb0e4c

```
The idea here is to save hash(plain-text+salt) in the database. Salt would be a randomly generated string per user. The login and register scripts could look like :

```java
Boolean register(username, password){
   salt = generateRandomSalt();
   hash = md5(password+salt)
   return saveInDb(username, salt, hash);
}

Boolean login(username, password){
   salt = getDbSalt(username);
   hash = getDbHash(username);
   return md5(password+salt) == hash;
}

```
This makes it harder for the attacker to find out trivial passwords since each user's password is appended with a random and different salt before hashing.


3. Hash + Salt + Pepper
------------------------
The previous approach definitely makes it very hard and expensive - in terms of computation, for attackers to isolate users with weak passwords. However, for a small user base, this won't be the case. Also, the attacker could also target a particular set of users without much effort. Long story short, the previous approach just made things harder, not impractical. This is because, the attacker has access to both hash and the salt. So, obviously the next step is to throw in another secret into the hash function - a secret that is not stored in the database, unlike the salt. Let's call this Pepper and this will be same for all users - a secret of your login service. Could be stored in your code or production servers. Anywhere but the same database as user info. With this inclusion, your login and register scripts could look like:

```java
pepper = "My-Secret-Pepper in codebase here"

Boolean register(username, password){
   salt = generateRandomSalt();
   hash = md5(password+salt+pepper)
   return saveInDb(username, salt, hash);
}

Boolean login(username, password){
   salt = getDbSalt(username);
   hash = getDbHash(username); // Obviously, you do these 2 in one Db read call
   return md5(password+salt+pepper) == hash;
}
```


Few remarks
------------------
The security of your system also depends on the type of hash function you use. The last method offers a fairly good level of security to user's password in the event of a data breach. Now the obvious question to ask at this point would be, how to upgrade from an existing system to a better one?


Upgrading your security design
-----------------------------
Imagine you saved all passwords as ```md5(password+salt+pepper)``` and now would like to change it to something like ```sha256(password+salt+pepper)``` or ```md5(password+salt+newpepper)``` - because you suspect that your old pepper isn't a secret anymore! An upgrade plan could look like :

 1. For each user, compute ```sha256(md5(password+salt+pepper)+salt+pepper)```
 2. Update login and register scripts as below

```java
// Previous script
Boolean register(username, password){
   salt = generateRandomSalt();
   hash = md5(password+salt+pepper)
   return saveInDb(username, salt, hash);
}
Boolean login(username, password){
   salt = getDbSalt(username);
   hash = getDbHash(username);
   return md5(password+salt+pepper) == hash;
}

// New scripts - notice the layers in hashing!
Boolean register(username, password){
   salt = generateRandomSalt();
   hash = sha1(md5(password+salt+pepper)+salt+pepper);
   return saveInDb(username, salt, hash);
}
Boolean login(username, password){
   salt = getDbSalt(username);
   hash = getDbHash(username);
   return sha256(md5(password+salt+pepper)+salt+pepper) == hash;
}

```

As you upgrade over time, you will have more layers in the hash function. Fun fact : Facebook does something similar with half a dozen layers, they are calling it [The Onion][fb-the-onion]


FYI
-----------------
There are more sophisticated ways of protection besides the above. Such as : Using [Secure multi-party computation][Secure_multi-party_computation], Isolated Key servers etc. 


[adobe-hack]: https://lastpass.com/adobe/
[Linkedin]: https://lastpass.com/linkedin/
[eHarmony-hack]: https://lastpass.com/eharmony/
[murphys-law]: https://en.wikipedia.org/wiki/Murphy%27s_law
[common-passwords]: http://www.passwordrandom.com/most-popular-passwords
[Secure_multi-party_computation]: https://en.wikipedia.org/wiki/Secure_multi-party_computation
[fb-the-onion]: https://twitter.com/filosottile/status/552830697942319105
