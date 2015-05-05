# Offering asparagus

From https://www.w3.org/wiki/Socialwg/Social_API/User_stories#Offering_asparagus

> 1. Farmer MacDonald advertises the availability of 100 kg of asparagus on his farm profile
> 2. Alice demands 20 cases
> 3. Bob demands 40 cases
> 4. Farmer approves Alice's demand of 20
> 5. Farmer replies to Bob's demand that he has only 20 cases left
> 6. Bob approves modified demand with 20 cases

## Demo

**TODO** *make possible to start local web server and open index.html*


## Illustration

**TODO** *draw diagram illustrating used architecture*

## Explanation

Real world deployment **SHOULD** use HTTPS and auth everywhere!

Based on:
* http://www.hydra-cg.com/spec/latest/schema.org/#rsvp-action
* http://schema.org/docs/actions.html
Relevant to:
*  http://www.w3.org/TR/web-payments-use-cases/#discovery-of-offer

```json
{
  "@context": "https://w3id.org/plp/v1",
  "@id": "http://graph.demo.hackers4peace.net/7c95e382-e1c8-420a-8776-e4b26c58347a",
  "@type": "gr:Offer",
  "name": "Offering 100kg of asparagous",
  "gr:includesObject": {
    "gr:amountOfThisGood": "100",
    "gr:typeOfGood": "http://aims.fao.org/skosmos/agrovoc/en/page/c_669",
    "gr:unitCode": "kg"
  },
  "operation": [
    { "@type": "Respond", "expects": "schema:Demand" }
  ]
}
```

```json
{
  "@context": "https://w3id.org/plp/v1",
  "@id": "http://graph.demo.wwelves.org/7c95e382-e1c8-420a-8776-e4b26c58347a",
  "@type": "gr:Demand",
  "name": "Requesting 20kg of asparagous",
  "inReplyto": "http://graph.demo.hackers4peace.net/7c95e382-e1c8-420a-8776-e4b26c58347a"
  "gr:includesObject": {
    "gr:amountOfThisGood": "20",
    "gr:typeOfGood": "http://aims.fao.org/skosmos/agrovoc/en/page/c_669",
    "gr:unitCode": "kg"
  },
  "operation": [
    { "@type": "Accept", "expects": "schema:Offer" }
    { "@type": "Respond", "expects": "schema:Offer" }
  ]
}
```
