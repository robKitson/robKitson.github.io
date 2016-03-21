---
layout: post
title:  "My Testing Philosophy"
date:   2011-10-01 00:00:00 -0800
categories: 
---
Whenever possible I write my tests first. I try to keep my tests small and focused on a particular behavior of the SUT (System Under Test, a.k.a. the class I'm currently testing). I tend towards unit tests that exercise my SUTs in isolation, using mock objects to control the interactions it may have with it's dependencies but also wrapping those interactions in helper methods within the SUT to avoid creating tests that have too much knowledge about the implementation of the method being tested.

Integration tests are crucial to ensuring that the system is working from end-to-end, but should be used sparingly due to the fact that they typically are: long-running, more difficult to setup, more brittle, and quick to increase in number and complexity. My typical integration test suite includes 1 happy-path test and 1 sad-path test (the most critical), while every 'contract' between classes will have tests for the interesting pre/post conditions.

On occasion, I'll write a throw-away test fixture who's sole purpose is exploratory testing of a new 3rd party library/module that I want to get familiar with before adding it to my project.