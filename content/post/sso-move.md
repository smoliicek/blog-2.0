+++
date = '2026-03-29T20:56:09+01:00'
draft = false
title = 'Setting up SSO on all of my self-hosted services'
+++

Recently, my mom came up to me, she forgot her NextCloud password again. It's not a problem, just jump into the admin user, and reset the password. But that got me thinking, would it be possible to set up an SSO, so everyone would just have one password and account for all of my self-hosted services?

## Motivation

Apart from the already mentioned password problem, there are a few more things.

* Adding users - Whenever I wanted to add a new account, I would need to login everywhere, and create the account manually. That wasn't a problem at first, but since I started self-hosting most of the services for my family, that meant more accounts, and we are back at the password problem.
* Security - Some of the services don't really have a secure login system (looking at you, immich), so I was just hosting them locally and accessing them through local IPs, but having something like NextCloud or immich public is something that is more important than I was thinking - I'd like to backup my photos even when I'm out, and access to my cloud files is a no-brainer

## But how?

I hear you asking, and I was asking the same thing. It would be possible to use something like Google SSO, but I don't like Google (or any other SSO provider for that matter). I could just use Cloudflare Access and email codes, but I already hear my users crying that they didn't get the code, and that's the last thing I want.

But, since I already self-host so much, what's one more service - I decided to use authentik.

## What I'm protecting

Before getting into it, let me quickly run through what I'm actually securing.
The main stuff me and my family uses are:

* NextCloud - our self-hosted and private GDrive replacement
* Immich - handles backup of everyone's phones
* Jellyfin - our media vault

Also the many smaller services and monitoring dashboards I use, that I'd rather not leave open to the world.

All of those need an account, all of those accounts need a separate password, and all of that was not fun to manage.

## How authentik ties it all

Setting up authentik was surprisingly easy for most of my services (some were a pain, looking at you, NextCloud), but with the documentation authentik provides, everything is manageable. Many services (like immich or Grafana) support SSO using OpenID Connect out-of-the-box, and those who don't generally have a plugin for it.

Something like Uptime Kuma sadly doesn't have either, but authentik comes in clutch, since you can use it as a Proxy!

Now when my family opens Nextcloud, they get automatically redirected to the authentik login page, they enter one password, and they're in. Same account, same password, and most importantly one 2FA everywhere.

### Authenticating using a second factor

We all hear it, you need to use 2FA everywhere, but try to explain to the non-tech savvy people that they need to keep a special app on their phone, and that everything they login to has a special code in the app.

Since authentik supports WebAuthn as a 2FA measure, it means that the second factor is putting a finger on the scanner, typing a PIN or scanning a face. Much easier to explain, and much simpler to everyone else.

## Pomerium - the service I didn't know I needed

Here's where my setup gets a little more involved than the average SSO guide.

You know the drill, you are away from home and you hear your phone ringing. "The server is on fire!" you hear from the other end. The server indeed was not on fire, but immich crashed when trying to process the 50 000 images that my family has taken that day. One command would fix this, however, I didn't have a way to connect to the host.

Pomerium currently fills this role, it exposes SSH to the public internet, however, instead of just requiring my SSH key, it also requires the SSO authentication. It's an extra layer of security, that costs me nothing, but gives me a peace of mind knowing, I can connect from anywhere, without needing to age 50 years trying to connect using a VPN.

## Conclusion

Looking back, the only thing I have done wrong is not setting this up sooner. Everybody who uses my services has one login to remember. I have peace of mind that every login hitting the public internet is secure.

I have one place to manage everything and as a bonus, a setup that grants me access to my local network from anywhere - no VPN, no panic. Just one ssh command away, from anywhere in the world.

If you're self-hosting more than 2 or 3 services for other people, I'd genuinely recommend looking into authentik. The initial setup takes an afternoon, but the payoff in security, usability and your own sanity is absolutely worth it.

Happy signing in! :)

-- Signed-off-by: smoliicek [\<me@smoliicek.cz\>](mailto:me@smoliicek.cz)
