+++
date = '2026-03-01T20:56:09+01:00'
draft = true
title = 'Setting up SSO on all of my self-hosted services'
+++

Recently, my mom came up to me, she forgot her NextCloud password again. It's not a problem, just jump into the admin user, and reset the password. But that got me thinking, would it be possible to set up an SSO, so everyone would just have one password and account for all of my self-hosted services?

## Motivation

Apart from the already mentioned password problem, there are a few more things.

1) adding users - Whenever I wanted to add a new account, I would need to login everywhere, and create the account manually. That wasn't a problem at first, but since I started self-hosting most of the services for my family, that meant more accounts, and we are back at the password problem.
2) security - Some of the services don't really have a secure login system (looking at you, immich), so I was just hosting them locally and accessing them through local IPs, but having something like NextCloud or immich public is something that is more important then I was thinking - I'd like to backup my photos even when I'm out, and access to my cloud files is a no-brainer

## But how?

I hear you asking, and I was asking the same thing. It would be possible to use something like Google SSO, but I don't like Google (or any other SSO provider for that matter). I could just use Cloudflare Access and email codes, but I already hear my users crying that they didn't get the code, and that's the last thing I want.

But, since I already self-host so much, what's one more service. I decided to use authentik.
