---
author: barinali
comments: true
date: 2015-12-23 20:30:44+00:00
layout: post
link: http://blog.alibarin.com.tr/e2e-testing-with-protractor-for-angular/
permalink: /e2e-testing-with-protractor-for-angular
title: E2E Testing with Protractor for Angular
wordpress_id: 137
categories:
- Angular.js
- Testing
tags:
- angular
- angularjs
- jasmine
- protractor
- qa
- selenium
- testing
---

I have been writing E2E test for a project that I am working on. And critical path on the project is the most important thing for us. And we have a ritual before every pull request. This ritual is critical path testing.

Our deployment cycle is like the following;




  1. open a pull request


  2. run a new vagrant environment with code that is in the pull request for preview/testing.


  3. **test the critical path** and new feature or bug fix.


  4. pass or fail the the pull request


As far as you see, there are just 4 steps for testing. And 1., 2., and 4. steps take short time. But third step takes respectable time. And it makes testing hard. Especially when there are a lot of tickets in the in QA column at Jira (By the way, we are developing with agile and scrum),  our project manager gets lost in it. And I think the PM need to test just new feature or bug fix for every pull request (on the order hand, that's a jira ticket too). But now, the PM test critical path and pull request content.

So I want to rescue my PM from this deadweight. Don't let it be misunderstood. Like I said, this deadweight is just testing for the critical path. Because I don't write test for new features or bug fixes yet.

Whatever.. I keep this theoretical story short. Let's talk technical.


## First, Protractor Installing


First, we have to install protractor as global. We can install protractor with this line; npm install -g protractor. When we installed protractor as global, webdriver-manager  command is installed. Now, we must update the web drivers for selenium. Then, we can use these commands.


## Initialise Config for Protractor


Now, we need a config file for running test(s). There is a example [config file](https://github.com/angular/protractor/blob/master/example/conf.js) for that. These config file contains these lines;


    exports.config = {
      directConnect: true,
      capabilities: {
        'browserName': 'chrome'
      },
      framework: 'jasmine2',
      specs: ['spec.js'],
      jasmineNodeOpts: {
        defaultTimeoutInterval: 30000
      }
    };




Protractor opens a chrome browser and runs spec.js for testing with this config. We can add another browser and open multi-browser for concurrent testing. And we can use another testing framework. Like Mocha, Cucumber or custom testing framework. You can look at [this page](http://www.protractortest.org/#/frameworks) for more information. Usually, I use mocha for testing. But protractor has limited support for Mocha.


## First Spec File


I hope you know Jasmine or another testing framework. Because we will make an example now. What will we test? Let's test a small part of AngularJS' official website.

Our test steps should be like these;




  1. AngularJS official website should be opened


  2. ngModel that is in "The Basics" should be typeable


  3. ngBind that is in "The Basics" should be updated


Our goal is "ngBind that is in **The Basics **should be updated." here. Our spec file will be like the following;


    var inputText = 'Ali Barın';

    describe('AngularJS Website', function() {
      it('should be opened', function() {
        browser.get('https://angularjs.org/');

        expect(browser.getCurrentUrl()).toContain('angularjs.org');
      });
    });

    describe('ngModel that is in "The Basics"', function() {
      it('should type into itself', function() {
        var $input = element(by.model('yourName'));
        $input.sendKeys(inputText);

        expect($input.getAttribute('value')).toBe(inputText);
      });
    });

    describe('ngBind that is in "The Basics"', function() {
      it('should be updated', function() {
        var $input = element(by.binding('yourName'));

        expect($input.getText()).toContain(inputText);
      });
    });



This test may be much better. But definitely it's enough for first step. Now, we can run tests with protractor protractor.conf.js  command.

I hope I will write a new post about multi capabilities on protractor, protractor on BrowserStack and maybe more when I am available.

PS: If there is something wrong or might be better, feel free to comment.
