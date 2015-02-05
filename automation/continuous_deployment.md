# Continuous deployment

## Goals

* Define deployment strategy
* Configure CI to deploy automatically

## Motivation

We can improve quality and productivity by decreasing the size of changes and increasing the frequency of changes. This is summed up in the phrase "release early, release often".

## Prerequisites

* Continuous integration
* Staging environment
* Canary environment
* Monitoring
* Alerting

## Steps

### Strategy

To the extent you are confident of your quality using only automated tooling, automate deploy promotion.

For example:
* If all tests pass, merge into master
* Deploy to staging
* Run tests against staging
* Deploy to canary
* Monitor canary
* Deploy to production
* Monitor production

### Configure

1. Configure CI to push to staging
1. Configure CI to push to canary
1. Configure CI to push to production

## Reflect

* Do you feel more confident?

## Related

* http://education.sys-con.com/node/318776
* http://www.startuplessonslearned.com/2009/06/why-continuous-deployment.html