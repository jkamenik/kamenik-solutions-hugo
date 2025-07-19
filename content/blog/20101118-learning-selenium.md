---
title: 'Learning Selenium'
date: 2010-11-18
lastmod: 2010-11-18

# Keywords help in classifying content
keywords:
  - Learning Selenium
  - HowTo
  - Learning
  - Selenium
  - Testing
---

My basic need is to find a platform where I can test FF, IE, and Safari on Windows, Linux, and OS X. I use OS X as my platform, and Safari or Webkit as my environment. I don't like Windows or IE. Linux is OK, but I like OS X because it just works the way I want. And I find FF to be slow, and Firebug which is needed to debug we pages causes rendering changes and timing issues (most notably causing FF to crash).

<!--more-->

Ideally I want the testing environment:

1. To be developed in Safari on OS X
2. To be able to test both internal libraries and rendered UI
3. To use unit tests to test internal libraries
4. To use interactive tests to test rendered UI
5. To use the unit/interactive tests as regression system moving forward
6. To write the tests once on my browser of choice
7. To run the tests on all combinations of browser and platform.
8. To not be bogged down by the testing framework
9. To be free, or very cheap

From my research it looked like Selenium did basically exactly what I needed. And unfortunately was the only real option. There were plenty of options for taking screen shots of public sites (which mine isn't, yet) and comparing those between browsers. And there are several options for unit testing javascript, but only Selenium did both and could be run on my own hardware.

## Implementation

From my reading it looked like I wanted to use the IDE to create the tests, and remote controls to run the browsers. Eventually I need to scale to Selenium Grid, but that is for later discussion.

### Test code

This is the sample file that I created to test.

```html
<html>
<body>
<script>
Namespace = {
	test: function(item){
		return item == true;
	}
};

function String(item){
	if(!item.push && typeof(item) === 'object'){
		return item.name || '';
	}
	return ''+item; //yup this is faster then toString
}

function Int(item){
	return parseInt(item,10);
}

function Array(item){
	var type = typeof(item);

	if(type === 'string'){
		return item.split("\\\\n");
	} else if(type === 'object'){
		if(item.push && item.length && item.concat){
			return item;
		}
	}
	return [item];
}
</script>
</body>
</html>

```

### Using the IDE

It took a long time to understand this tool, since I had no background in Selenium. The basic premiss is that each file is a single test case, which is a set of tests. Each test is a grouping of three items: the action, the target, and the expected result. It natively creates a 3 column HTML table, which it can also run, but personal preference is that use the IDE to export the basic test into a different language.

I am a rails developer, and am familiar with rspec so I use the IDE to run the tests to make sure they work, but then I transfer it to rspec since it is a more expressive test framework. The downside is that you have to use a Remote Control to run the test, which adds an extra level of complications. We will get to the Remote Control later.

A basic HTML test looks like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "<http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd>">
<html xmlns="<http://www.w3.org/1999/xhtml>" xml:lang="en" lang="en">
<head profile="<http://selenium-ide.openqa.org/profiles/test-case>">
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<link rel="selenium.base" href="file:///Users/jkamenik/Desktop/sel_test.html" />
<title>Unit Testing</title>
</head>
<body>
<table cellpadding="1" cellspacing="1" border="1">
<thead>
<tr><td rowspan="1" colspan="3">Unit Testing</td></tr>
</thead><tbody>
<tr>
 <td>open</td>
 <td>file:///Users/jkamenik/Desktop/selenium/sel_test.html</td>
 <td>test</td>
</tr>
<tr>
 <td>verifyEval</td>
 <td>this.browserbot.getUserWindow().Int(1)</td>
 <td>1</td>
</tr>
<tr>
 <td>verifyEval</td>
 <td>typeof(this.browserbot.getUserWindow().Int(1))</td>
 <td>number</td>
</tr>
</tbody></table>
</body>
</html>

```

There really is nothing more to it then that. The one thing to note is that the test uses `verifyEval` which takes a JavaScript string.

> [!NOTE]
> In all tests the this object is the base Selenium object so if you want to get to the window object you have to traverse up the stack via `this.browserbot.getUserWindow()`.

> [!WARNING]
> Unfortunately everything tested in Selenium is converted to a string before testing. So if I need to ensure that an integer parsing function actually produces a number I need to use typeof.

## Using RSpec

The IDE is a great way to test scripts live, but for any programmer it is going to be easier to use a testing framework doing it programmatically. As a rails guy I prefer RSpec so that is what I use.

### Installing

This package requires ruby-gems, rspec, and selenium-client. I am going to assume you have ruby-gems installed already. The others are installed like this:

```bash
sudo gem install rspec
sudo gem install selenium-client

```

### Converting

When using Rspec the only real thing to remember is that there are no assert* or verify* methods. The reason is that Rspec itself is a testing framework so it will have it own version of assert and verify (in this case should).

The IDE has a great feature in that it converts the HTML test into a rspec test for you. It isn't a great format, but it is better then nothing and is a good place to start.

```ruby
require "rubygems"
gem "rspec"
gem "selenium-client"
require "selenium/client"
require "selenium/rspec/spec_helper"
require "spec/test/unit"

describe "array_test" do
attr_reader :selenium_driver
alias :page :selenium_driver

before(:all) do
  @verification_errors = []
  @selenium_driver = Selenium::Client::Driver.new \\\\
    :host => "localhost",
    :port => 4444,
    :browser => "*chrome",
    :url => "file:///Users/user/Desktop/selenium",
    :timeout_in_second => 60
end

before(:each) do
  @selenium_driver.start_new_browser_session
end

append_after(:each) do
  @selenium_driver.close_current_browser_session
  @verification_errors.should == []
end

it "test_array_test" do
  page.open "file:///Users/jkamenik/Desktop/selenium/index.html"

  begin
    ("1").should == page.get_eval("this.browserbot.getUserWindow().Array([1])")
  rescue ExpectationNotMetError
    @verification_errors << $!
  end

  begin
    ("object").should == page.get_eval("typeof(this.browserbot.getUserWindow().Array(1))")
  rescue ExpectationNotMetError
    @verification_errors << $!
  end
end
end

```

> [!WARNING]
> The browser being shown is `chrome`. This actually means Firefox, not Google Chrome. For Google Chrome use `googlechrome`.
>
> For Safari use `safari`, but remember that you will need to disable the popup blocker manually and close Safari (for this user) otherwise it will just sit there forever.

### Remote Controls

A remote control is what Selenium uses to execute the test. The IDE comes with it built-in, but it is tied to FireFox. To use IE, Safari, or Chrome you need to download the remote control software: [http://seleniumhq.org/projects/remote-control](http://seleniumhq.org/projects/remote-control). This software is just a Java server that opens your machine on port 4444 (by default) to allow Selenium clients to run tests. Each client gets its own browser instance to run the tests in.

> [!NOTE]
> The server must be run by a user that has access the browser and has a screen to render to.

> [!WARNING]
> Firefox will only run a single profile per user. If you need to run Firefox concurrently on the same machine you need to fake a second profile. Don't do it, just create a VM; you will be happier.

> [!CAUTION]
> Google Chrome does not works on OS X. This is because OS X doesn't add application executables to the path, and the server code isn't smart enough to use the executable directly. The fix is supposedly here, but I was not able to get it to work. If I do I will probably write another blog entry and link it here.

### Putting it all together

By default RSpec provides no runner code and the code the IDE produces is not standalone. This is not a problem since installing RSpec into a rails app installs script/spec. I have copied the runner code here so make it easier.

```ruby
#!/usr/bin/env ruby
if ARGV.any? {|arg| %w[--drb -X --generate-options -G --help -h --version -v].include?(arg)}
  require 'rubygems' unless ENV['NO_RUBYGEMS']
end
require 'spec/autorun'
exit ::Spec::Runner::CommandLine.run

```

I am going to assume the RSpec runner code is called spec and the test file is called test.rb. To run this test from the command line do the following:

```bash
ruby spec test.rb
```

Assuming you followed all the steps the test should have opened Firefox, executed a page, run the tests, closed Firefox, and returned the results. Now you can add more tests and have Selenium execute them.

## Related Research

1. Using Selenium Grid
2. Using Chrome, or IE
3. Using a Grid to run the same test in all browsers on all OSs
