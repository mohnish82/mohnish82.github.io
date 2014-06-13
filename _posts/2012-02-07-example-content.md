---
layout: post
title: Gigaset dial plan with Google Voice, Localphone and Callcentric
---

-----

<img style="float:right" src="/images/gigaset-c610ip.jpg" />
I use Gigaset C610-IP VOIP phone for my calling needs. I’ve hooked it up to Google Voice (using [Simonics](https://simonics.com/gvgw/) gateway) for free US calling. For my international (India) calling needs, I was using [Localphone](http://www.localphone.com/) exclusively until recently. But as Localphone’s call quality decreased to sub par levels, I started looking around for alternatives. I could use Google Voice that cost just 2c/min but with Google declaring that they’ll shut down integration with 3rd parties, I looked around and settled on [Callcentric](http://www.callcentric.com/). Callcentric costs 2.4c/min to India and the voice quality is excellent.

As both Google Voice and Localphone, support E.164 number format i.e. international code +  area code + number, I never had the need to worry about dial plans and other stuff. I stored India numbers as 91xxxxxxxx and US numbers as either 1xxxxx or 10 digits directly without the 1. In dialing plans, I choose the setting – If number starts with 91 use Localphone, otherwise use Google Voice. This worked pretty well as Google Voice accepts 1xxxxx and 10 digit numbers for USA.

But with Callcentric added to the mix, I faced issues because it does not support ENUM format. Dialing 91xxxx, is not sufficient to call India! I must dial 01191xxxxx. Didn’t took long to figure that Gigaset offers very limited dial plan configuration options. But eventually, found a way to make it all work with the following settings:

* `Management > Local Settings`: Choose country as USA and both international and local `Code Number` as 1. Select `Yes` for the option `Predial long distance access code for VoIP calls`.
* `Telephony > Dialling Plans`: Declare 2 dial plans i.e. 91 — Callcentric  &  1 — Google Voice. Do not select `Use Area Code` option for both. Then under `Code for VOIP line`, enter 011 and choose `Always`.
* Choose `Google Voice` to be the default call out line.

What this accomplishes is that any dialed number starting with 91 or 1, gets 011 appended to it. 91xx to 01191xx helps to satisfy the Callcentric requirement, so India calling works fine. 1xx to 0111xx works fine as Google Voice accepts 011 + country code + number format. So, 0111<US 10 digit number>, works with Google Voice. You may be wondering that if area code is not to be selected then why did we use that option in 1. That option allows us to dial 10 digit US numbers i.e. without the 1 prefix and still make calls through Google Voice. The way it works is that seeing 10 digit number (not starting with 1), the area code triggers-in. So, it makes US 10 digit number 11 digit number by prefixing 1. Then the dial plan appends 011 to it, making it 0111<US 10 digit number>, which works with Google Voice!

Earlier I thought that due to the limitations of dial plan configuration, I’ll have to go the SipSorcery route. But this configuration works well for dialing international and US numbers (whether 1 prefixed or not). Happy with the current setup for now.

-----

Want to see something else added? <a href="https://github.com/mdo/hyde/issues/new">Open an issue.</a>
