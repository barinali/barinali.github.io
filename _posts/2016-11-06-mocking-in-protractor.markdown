---
author: barinali
comments: true
date: 2016-11-06 00:00:00+02:00
layout: post
link: http://blog.alibarin.com.tr/mocking-in-protractor/
permalink: /mocking-in-protractor
title: Mocking in Protractor
meta_description: Mocking in Protractor
categories:
- Angular.js
- Testing
tags:
- angularjs
- protractor
- testing
excerpt: Now, our subject is how to mock requests which go out from our web application.
---

I had written two posts about protractor and E2E testing. Then I had started to write this post. But I couldn't find time to complete this.

Anyway. Now, our subject is how to mock requests which go out from our web application. These requests can be created by $http or something else. It doesn't matter. There is just a thing which matters this web application should be built by AngularJS. Normally, we can use protractor with non-AngularJS websites for testing. But when we need to mock something, we need an application which is built with AngularJS in this case.

I assume you have a web application which is built by AngularJS. I will use a backend mock module which is <a href="https://github.com/nchaulet">nchaulet</a>/<a href="https://github.com/nchaulet/httpbackend">httpbackendfor</a> for mocking our requests. This module makes our work easier.

I will skip over how to install the module. You should already know that.

After installation, we need to add this module our tests files the following;

{% highlight javascript linenos %}
  var Backend;

  beforeAll(function() {
    // Before everything, preparing mocks.
    Backend = new HttpBackend(browser);

    Backend.whenGET(/users\/me/).respond({ username: 'barinali', email: 'iam@alibarin.com.tr' });
  });
{% endhighlight %}

After this, when our application sends a request to /users/me, it will get a response which is like above. If you don't want to use httpbackend module, you must write your mock module.

For example;

{% highlight javascript linenos %}
  var outerResponse = { key: value };

  browser.addMockModule('httpBackendMock', function() {
    var response = arguments[0];

    angular.module('httpBackendMock', ['ngMockE2E'])
      .run(function ($httpBackend) {
        console.log(response); // { key: value }
      });
  }, outerResponse);
{% endhighlight %}

If you're working with large response body, you may need a <a href="https://github.com/angular/protractor/issues/3212#issuecomment-226775294">workaround</a> for working with them. Because there is an <a href="https://github.com/angular/protractor/issues/3212">issue</a> which is closed and not fixed.

In this post, I just wanted to shed light on this topic. I hope this helps.
