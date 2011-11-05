# monitors.txt

## What is monitors.txt?
A text file that lives at www.yoursite.tld/monitors.txt and describes in plain language what monitoring you want done on your site.
Your monitoring provider regularly reads your monitors.txt file to configure your application's monitors. Due to the open nature of monitors.txt,
you'll be able to migrate or even add new monitoring services with very little manual setup.

One intention of monitors.txt is to encourage developers to improve monitoring for their web sites by making it easy to setup new monitors;
I don't enjoy logging into some monitoring service web app to setup monitors, but I do enjoy writing readable monitoring tests right there in my code.

## What if I want to keep my monitor configuration private?
You write your monitors in the same human-readable language, but restrict access to the file so only your monitoring provider can read it.

## Show me a sample monitors.txt already

A basic monitors.txt file for monitorstxt.org :

	# monitors.txt - see http://monitorstxt.org for more info
	Scenario: The monitorstxt.com domain should redirect to monitorstxt.org
		When I visit http://monitorstxt.com
		Then I should be redirected to http://monitorstxt.org

	Scenario: The home page should show the sample monitors.txt file
		When I visit http://monitorstxt.org
		Then I should see "The home page should show the sample monitors.txt file" within "body"

	Scenario: DNS should resolve monitorstxt.org to the correct IP address
		When I use DNS to lookup monitorstxt.org
		Then I should see the IP address 1.2.3.4
		
And something with a few more bells and whistles :

	# monitors.txt - A sample monitor for DuckDuckGo
	
	# Feature information is optional
	Feature: DuckDuckGo Search
	  It should continue to kick ass
	  And I should be able to search

	  Scenario: Search over SSL
	    When I go to https://www.duckduckgo/
	    And I fill in "q" with "site:news.ycombinator.com"
	    And I press submit
		Then I should be on https://duckduckgo.com/?q=site%3Anews.ycombinator.co    
		Then I should see "Hacker News" within "h2"

## monitors.txt looks a lot like a Cucumber feature
monitors.txt ought to be flexible and easy to read, hence why I've gone with this format. Alternative formats to Cucumber's Gherkin ought to be supported if needed.

## Feedback wanted
monitors.txt is a work in progress that I'd love your feedback on. Contact eliotsykes -at- gmail or discuss on Hacker News.
