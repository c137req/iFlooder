# iFlooder
iFlooder, the provider for email and phone harassment. It is essentially a project that shows how an attacker, ex-boyfriend, ex-girlfriend, literally anyone can sign you up for something without your permission. Commonly, usecases for platforms are diverse and almost 99% of the time these systems are abused. This repository contains code that automates and facilitates this abused process to show how _easy_ it is to abuse services to harass your every-day average Joe.

Tl;dr this allows for essentially what is a decentralised collection of SMTP servers to send a bunch of emails to your inbox unintentionally fulfilling the attacker's intentions.

## Methodology
1. Newsletters
    - newsletters are an amazing way to spam somebody's inbox if enough are registered to
    - guaranteed consistent emails (unless target contacts to get themselves blacklisted)
    - often ZERO anti-bot (when there is it is very easy to bypass)
2. Government form sign-ups
    - also often zero anti-bot which is weird/funny because it feels to me like this should be a must for government services/sites with form inputs
    - will NEVER go to spam
    - will scare the target
3. Military +/ army recruitment
    - also will never go to spam
    - will scare the target
    - can affect real-life for target

## Reiteration of "the point of all this"
1. show how automated systems can be abused when proper authentication doesn't exist
2. fun
3. allows me to prove to myself I'm better than somebody else with seleniumBASE and robust code in general
4. i want to convince services to force PGP auth/verification

I believe that if providers services force PGP for signup and login as MFA instead of TOPT via secret code (usual form of 2FA) as its not only **easier** but also much more **efficient** in the long run. PGP is credible and reliable. Its not one-way encryption. Its not STUPID like elon musk and other public figures. But seriously, systems are abused every day for harassment and I want security, and this repository will serve as a proof-of-concept for how truly bad harassment can become when automated.

## To Do's
- create API
  - `/v1/` will be the route for the following:

    email endpoints
    - `/email`                   - 302, redirect -> `/health`
    - `/email/send/:email/`      - 510, response -> "append `/:site` or `/all`"
    - `/email/send/:email/:site` - 200 if available, response -> 200 + "Sent" if sent
    - `/email/send/:email/all`   - 200 if available, response -> 200 + "Sent" if sent
   
    - cba doing phone endpoints rn but pretty much the same

- create modules for at least 10 unique sites
  - all endpoints findable (2fa, forgot password, create account, login, preference's - they usually have 'receive marketing emails...')

    In order to check all endpoints, what we'll be doing is:
    - using [xnLinkFinder](https://github.com/xnl-h4ck3r/xnLinkFinder) to find all possible endpoints we can
    - manual searching (signing up, logging in, etc)

      Sometimes manual searching won't 'yeild' an endpoint as it may use templates (check for SSTI always lolol), which is why we will be integrating SeleniumBASE and using the headless browser support to stay CLI
