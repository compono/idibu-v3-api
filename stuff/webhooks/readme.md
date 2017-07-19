# What is a webhook?

A webhook is an API concept that’s growing in popularity. As more and more of what we do on the web can be described by events, webhooks are becoming even more applicable. They’re incredibly useful and a resource-light way to implement event reactions.

So, what exactly is a webhook? A webhook (also called a web callback or HTTP push API) is a way for an app to provide other applications with real-time information. A webhook delivers data to other applications as it happens, meaning you get data immediately. Unlike typical APIs where you would need to poll for data very frequently in order to get it real-time. This makes webhooks much more efficient for both provider and consumer. The only drawback to webhooks is the difficulty of initially setting them up.

Webhooks are sometimes referred to as “Reverse APIs,” as they give you what amounts to an API spec, and you must design an API for the webhook to use. The webhook will make an HTTP request to your app (typically a POST), and you will then be charged with interpreting it.

Correctly coding the system to scale like this will save a lot of time in the long run.

[Source](https://sendgrid.com/blog/whats-webhook/)

# How to activate a webhook in idibu?

[[http://www.idibu.com/img/clientportal_logos/wk_generals.png]]


1. Vacancy - Vacancy created or updated
2. Attract - Candidate attraction events
3. Search - Talent pool searches ran
4. Candidate - Create or updated candidate records
5. Candidate extended - Full profile data sent
6. Users - User profile activity (login)
7. Post - Post and repost advert
