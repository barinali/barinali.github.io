---
author: barinali
comments: true
date: 2015-12-23 22:45:31+00:00
layout: post
link: http://blog.alibarin.com.tr/e2e-testing-with-protractor-on-browserstack/
permalink: /e2e-testing-with-protractor-on-browserstack
title: E2E Testing with Protractor on BrowserStack
meta_description: E2E testing on BrowserStack by using Protractor
categories:
- Angular.js
- Testing
tags:
- angularjs
- browserstack
- protractor
- reporter
- seleniumb
- teamcity
- testing
---

Previously, I have written one more post about this subject. But that is about initialise an E2E test with just one example spec file.

I will write about the followings in this post;

  1. How to run multi browsers
  2. How to run on BrowserStack
  3. How to export test result for TeamCity

## 1. How to run multi browsers

We have to use multiCapabilities keyword instead of capabilities in our protractor config for running multi browsers. But how?

{% highlight javascript linenos %}
multiCapabilities: [
  {
    'browserName': 'chrome'
  },
  {
    'browserName': 'firefox'
  }
]
{% endhighlight %}

I mean the config file will be like that;

{% highlight javascript linenos %}
exports.config = {
  directConnect: true,
  multiCapabilities: [
    {
      'browserName': 'chrome'
    },
    {
      'browserName': 'firefox'
    }
  ],
  framework: 'jasmine',
  specs: ['spec.js'],
  jasmineNodeOpts: {
    defaultTimeoutInterval: 30000
  }
};
{% endhighlight %}

We can use these keywords as a browserName; android, chrome, firefox, htmlunit, internet explorer, iPhone, iPad, opera, or safari.

## 2. How to run on BrowserStack
It isn't as hard as it seems. We need to add just three more keys in config. browserstack.user  and browserstack.key into every capability and seleniumAddress into config. It's enough for running tests on BrowserStack. I need to inform that. We have advanced environment when we use BrowserStack for this job. So don't restrict ourself. We can use different OS (with as any version as possible), browser version, and device! This list can be seen at [here](https://www.browserstack.com/list-of-browsers-and-platforms?product=automate). By the way, BrowserStack's seleniumAddress  is http://hub.browserstack.com/wd/hub.

There is a wizard for making os, browser, and resolution combination at [here](https://www.browserstack.com/automate/capabilities#capabilities-parameter-override). And you can find detailed configs for BrowserStack at [here](https://www.browserstack.com/automate/capabilities#capabilities-parameter-override).


## 3. How to export test result for TeamCity


There is a npm package named [jasmine-reporters](https://github.com/larrymyers/jasmine-reporters). I use this package for exporting test results. This package contains several different reporters. But I use TeamCity reporter. Because we use TeamCity on the project for CI.

First, we have to install this package with npm install jasmine-reporters --save. Then, we can use it in onPrepare function in config. This function runs before tests run. Thus, we can add our new reporter into protractor. We need to add these lines into config for this.

{% highlight javascript linenos %}
onPrepare: function() {
  var jasmineReporters = require('jasmine-reporters');
  jasmine.getEnv().addReporter(new jasmineReporters.TeamCityReporter());
}
{% endhighlight %}

Then, TeamCity will automatically catch this test results. And it will show that results on every build's page.


## Finally


We can run tests on BrowserStack and export results for TeamCity.

Maybe I continue to write within this post. Or I write another post about testing.
