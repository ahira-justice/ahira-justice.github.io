---
layout: post
title: "Licensing a Desktop Application and the Cryptography That Powers It"
date: 2020-06-04
---

Licensing a desktop application is hard, and cryptography is hard — at least it was for me when designing the licensing scheme for my company's desktop application. The difficulty of this task is largely dependent on the constraints placed on the licensing scheme. In my case, I had to find a way to license each user copy without an internet connection. This is considerably more challenging than going the online route — using token authentication coupled with user permissions to verify users and restrict features.

There are many reasons why licensing without an internet connection is a bad idea, and most companies choose to build web applications as a result. This article is for those times when your application definitely has to be deployed to the desktop.

Keep in mind that no licensing scheme is 100% effective. Also, keep in mind that there is a fine line between protecting your software from people who would rather not pay for it and pissing off your paying customers. With every layer of security and copy protection you apply, you risk losing a legitimate user.

I will be describing my approach within the constraints I was dealt, and at the end taking a look at the extra layers of protection you could apply, per some select use cases. Let me detail out the licensing requirements:

- Ensure only paying customers can use the software
- Assume users have poor or no internet connection
- Ensure the license can expire

So the most pertinent question became, how can I create a license on the server and have it verified on the client application without communication between them? Let me introduce you to asymmetric cryptography!

## Asymmetric Cryptography

Asymmetric cryptography is a cryptographic system that uses a pair of keys, a public key and a private key. The public key is called the encryption key and the private key is called the decryption key. They are so called because the public key can be distributed widely and used by anyone to encrypt secrets, to be decrypted only by the private key.

This system allows us to do a few interesting things, one of which is signature and verification. You see, the signature and verification process is the opposite of the encryption and decryption process. You sign a secret with the private key and each one of the numerous parties holding the public key can verify that the message came from the private key holder and the private key holder alone.

## Licensing Scheme

The signature and verification process allows us to design an offline licensing scheme. We generate a pair of asymmetric cipher keys, sign a unique dataset on the backend using the private key, and ship our desktop application with the public key.

The license key consists of the signature and the dataset in plain text. We verify the signature against the dataset to ensure that the license information has not been modified or tampered with. This dataset can contain license information such as user email address, time of license generation, license expiry date or validity period, and permissions information. With this verified information, we can make decisions in key areas of our application and we can revoke access once a license expires.

There is a lot more work needed to implement a licensing scheme, most of it is dependent on what language(s) you build with and what cryptography libraries are available, but the core idea remains the same. 

## Extra Protection

While the public key is open to everyone, as long as our private key is secure on our server and we use a sufficiently large key size, we protect against [keygens](https://en.wikipedia.org/wiki/Keygen). One way to counteract keygens is to change the cipher key pairs on every different version of your software. This adds some complexity since you now need to generate one key per version of your application. This is not an ideal solution but there are suitable workarounds.

This licensing scheme does not protect against [software cracks](https://en.wikipedia.org/wiki/Software_cracking) though, and honestly nothing can. Anyone with a copy of your application can take a decompiler or debugger to your code and go to town. We can make the process more difficult by obfuscating our code.

We can also incorporate a one-time internet connection to our offline licensing scheme. This way, we can for instance track the number of computers using the same license. This feature introduces its own class of complexities which I won't discuss in detail here.

## End-notes

There are a lot of details I have omitted or simplified in this article. This article is not a substitute for the experience of a security professional. Improper implementation of licensing algorithms can lead to revenue loss from theft or leave you with a lot of disgruntled users.

If you would like a more in-depth, technical discussion, I will be publishing an implementation specific version of this article soon.
