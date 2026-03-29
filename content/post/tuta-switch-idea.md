+++
date = '2026-03-28T21:00:13+01:00'
draft = false
title = 'Switching email providers, again'
+++

Renewal time. That's usually when I start questioning my life choices, at least the email-related ones.

I've been a Tuta user for almost a year now. However, there are some things that have been bugging me, and since I have to decide soon anyway, I think it's a good time now to look back and reassess.

## Background

Before we dive in, some context - I switched from Gmail to Tuta in [April of 2025](https://smoliicek.cz/post/moving-mails/). Then, I was choosing between Proton, Tuta, Fastmail, Mailfence and Zoho. Some (like Zoho and Fastmail) aren't hosted in countries that respect my privacy, so I crossed them off. At the end, I was choosing between Tuta and Proton (and ultimately chose Tuta).

Now, since I'm again a bit smarter this year, I have a new list of providers I could switch to. Before anyone asks, my stance to Proton is pretty negative, I don't really like how they do things. I don't have anything against people who use them, and my stance can also change. However, today, Proton will not be an option for me.

## Retrospective about my last switch

My last switch of email providers was... something. It was rushed, since I had only a few days before all my emails would stop hitting my inbox. Since I wasn't using an email alias (I had the one I use now, just wasn't using it), I needed to reconfigure EVERY service I use, and update all my contacts with my new email address.

Google eventually did nothing, and even though I didn't send them my ID, my emails kept coming and some emails from stray services still sometimes come to my Gmail inbox. However, the damage was done.

You can read more about my decision [here](https://smoliicek.cz/post/moving-mails/).

## About Tuta

Before I even start, I want to say that Tuta is an excellent email provider. It's really secure and respects your privacy. When I look back, Tuta was a good choice.

Things I like about Tuta:

* It's the only email provider to date that encrypts the subject of your message (when both parties use Tuta).
* Tuta encrypts your whole mailbox.
* They are based in Germany and have a strong no-logging policy.
* The support is the greatest I have ever seen. I never waited more than a few hours for their reaction.
* Once an address is registered, it cannot be taken by anyone else (even if you cancel your account)

There are also some things I don't like:

* Lacks GPG support.
* Their encryption is excellent, however, it works only when the other party is also using Tuta.
* I cannot use any other email client than theirs.
* The search is slow.

That brings me to what I'm looking for in a new email provider.

## My preferences

I'll get to the list shortly, but first, some of my preferences.

### GPG

In my original post, I stated:
> I know, I know, it doesn’t support PGP, but nothing is stopping me from encrypting the message myself and sending it like that, is it?

I was VERY wrong. At that time I didn't need to encrypt/sign much with PGP, so it didn't really matter to me. However, now that I'm contributing in the open source community, PGP has become something I use on a daily basis. Clear-signing sometimes breaks, since every mail client formats the text a little differently (and sometimes adds trailing new lines, which PGP isn't happy about). Currently I've been attaching the clear-signed message or the detached signature with the email. However, that is a hassle for me, since I need to write it elsewhere - sign it - copy to Tuta - attach signatures - send.

This is automatic in every other email I own, since Thunderbird autosigns everything and just asks me to put my finger on my Yubikey.

### Encryption of my mailbox

This is another thing that I like about Tuta, and if I move, I need this in my new mailbox. Encrypting incoming messages on the fly. It would be fantastic if this could also use PGP, but I will not complain if it doesn't.

### IMAP support

I really like the Tuta app. I think it's great and works well. However, the lack of GPG support officially, and not being able to take my email to another app really sucks.
I get why it's done this way, and I frankly don't like the way Proton does things (the bridge you need to run). What I'm looking for is native IMAP support, no bridges and no workarounds.

### Auto sorting and folders

Since the Tuta search isn't great (especially when searching for older emails) I started to really organise my inbox and I fell in love with it. Everything gets its own folder, so I mostly don't use the search function.

I'd like to keep the ability to organise my emails.

### Aliases with my own domain

When I moved to Tuta, I didn't set my main address everywhere, I set up my [me@smoliicek.cz](mailto:me@smoliicek.cz) as an alias and then used that. In retrospect, that was an excellent idea, since now, if I decide to move it will be easier.
That said, for it to be easier, the new provider obviously needs to support it.

## Comparing providers

| Feature | Tuta | mailbox.org | Posteo | Mailfence | Self-host | Proton |
|:---|:---:|:---:|:---:|:---:|:---:|:---:|
| GPG support | No | Yes | Yes | Yes | Yes | Yes |
| IMAP | No | Yes | Yes | Yes | Yes | Partial |
| Mailbox encryption | Yes | Yes | Yes | Partial | Yes | Yes |
| Folders | Yes | Yes | Yes | Yes | Yes | Yes |
| Custom domain | Yes | Yes | No | Yes | Yes | Yes |

I will talk more about each provider in the order they are listed.

### Tuta

It's the first one that comes to mind, not switching is also a choice and I think it's good to have something to compare to.
Technically I could continue working around the lack of IMAP and GPG support, but I set out to fix exactly these pain points, so staying feels like giving up on that.

### Mailbox.org

A provider I didn't even consider last time. It does everything I want it to. Some things to note, their inbox encryption relies on PGP, which means providing them with your private key so you can decrypt it in the web client. It's a trust trade-off worth being aware of.

> [!NOTE] NOTE
> You can skip uploading your private key entirely, just retrieve the encrypted mail via IMAP and decrypt locally in Thunderbird with your locally stored key.

### Posteo

Oh, Posteo, it sure is compelling. It supports proper E2E encryption, supports IMAP, GPG and has full inbox encryption, however it does not support custom domains - that is a deal breaker for me.

### Mailfence

I crossed Mailfence out with these words last time:
> I also wanted something that at least 3 people know of (joke, don’t come at me), so MailFence is also out.

However today, it seems like a good option. It supports everything, however the inbox encryption is a bit lacking, it only encrypts emails you manually set as encrypted with PGP.

### Proton

I know, I said it wouldn't be an option. But it still is a big provider in the privacy scene, so I'm including it for completeness' sake.

It supports everything, but partially... The need to run a separate app to use IMAP makes me just want to ditch it all together. It also means I can't use Thunderbird on my phone. It's something I cannot stand and just don't want to deal with.

### Self-host

It is a consideration for me. I like hosting stuff, everything I want is supported by self-hosting. However, I'm still a "newbie" in the self-hosting world and I don't trust myself running something as important for me as email myself

## What's next?

Currently, **mailbox.org** is my top candidate. It checks every box, and the PGP/IMAP story is exactly what I've been missing with Tuta.

That said, I'm not ready to flip the switch just yet. Email is a really big part of my life and work, switching email providers isn't something I want to rush _again_. My plan now is to run Mailbox alongside Tuta for a while to get a feel for it and also see how it holds up in my day-to-day use.

When I make my choice, and decide where/if to switch, I'll make a follow-up post about the migration process and how it went.

Until then, happy emailing!

-- Signed-off-by: smoliicek [\<me@smoliicek.cz\>](mailto:me@smoliicek.cz)
