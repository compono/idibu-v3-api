# What is a webhook?

A webhook is an API concept that’s growing in popularity. As more and more of what we do on the web can be described by events, webhooks are becoming even more applicable. They’re incredibly useful and a resource-light way to implement event reactions.

So, what exactly is a webhook? A webhook (also called a web callback or HTTP push API) is a way for an app to provide other applications with real-time information. A webhook delivers data to other applications as it happens, meaning you get data immediately. Unlike typical APIs where you would need to poll for data very frequently in order to get it real-time. This makes webhooks much more efficient for both provider and consumer. The only drawback to webhooks is the difficulty of initially setting them up.

Webhooks are sometimes referred to as “Reverse APIs,” as they give you what amounts to an API spec, and you must design an API for the webhook to use. The webhook will make an HTTP request to your app (typically a POST), and you will then be charged with interpreting it.

Correctly coding the system to scale like this will save a lot of time in the long run.

[Source](https://sendgrid.com/blog/whats-webhook/)

# How to activate a webhook in idibu?

Webhook management page can be found in idibu's general settings, under the "webhook settings" tab. The green button is used to add a new webhook:

<img style="display: block; margin-left: auto; margin-right: auto;" src="http://www.idibu.com/img/clientportal_logos/wk_generals.png" alt="" />


<img style="display: block; margin-left: auto; margin-right: auto;" src="http://www.idibu.com/img/clientportal_logos/wk_webset.png" alt="" />

<img style="display: block; margin-left: auto; margin-right: auto;" src="http://www.idibu.com/img/clientportal_logos/ad_webhook.png" alt="" />

Let's go through the fields, shall we?

__Payload URL__ - the URL where the webhooks will be sent. We reccomend using [https://requestbin.com/](https://requestbin.com/) for testing.

__Content type__ - define the format of the webhooks sent. It's either a json or x-www-form-urlencoded.

__Secret__ - non-required parameter you can add to authenticate your own requests. You can append it with SSL verification.

__Content sent__ - You can either have all events sent to the provided URL or you can choose from the following. Please note that this list contains links to pages that show example payloads sent:

1. [Vacancy](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/webhooks/vacancy.md) - Vacancy created or updated
2. Attract - Candidate attraction events.
3. Search - Talent pool searches ran.
4. [Candidate](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/webhooks/candidate.md) - Candidate create or updated.
5. Candidate extended - Full profile data sent.
6. Users - User profile activity (login).
7. Post - Post and repost advert.

besides that you can de-activate and re-activate your hook using a dedicated checkbox. This page also contains a log of a recent hooks send and will show errors, if those are encountered!

# Webhook responses - how should the listening script react after receiving a hook?

Your webhook acknowledges that it received data by sending a 200 OK response. Any response outside of the 200 range will let idibu know that you did not receive your webhook. idibu has implemented a 5-second timeout period and a retry period for subscriptions. We wait 5 seconds for a response to each request, and if there isn't one or we get an error, we retry the connection to a total of 19 times over the next 48 hours. A webhook will be disabled if there are 19 consecutive failures for the exact same webhook. 

If you're receiving a idibu webhook, the most important thing to do is respond quickly. There have been several historical occurrences of apps that do some lengthy processing when they receive a webhook that triggers the timeout. This has led to situations where webhooks were removed from functioning apps.

To make sure that apps don't accidentally run over the timeout limit, we now recommend that apps defer processing until after the response has been sent.

