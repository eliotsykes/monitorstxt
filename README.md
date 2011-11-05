# monitors.txt

## What is monitors.txt?
A text file that lives at www.yoursite.tld/monitors.txt and describes in plain language what monitoring you want done on your site.
Your monitoring provider regularly reads your monitors.txt file to configure your monitors. Due to the open nature of monitors.txt,
you'll be able to migrate or even add new monitoring services with very little manual setup.

The intention of monitors.txt is to encourage developers to improve monitoring for their web sites by making it easy to setup new monitors;
I don't enjoy logging into some monitoring service web app to setup monitors, but I do enjoy writing readable monitoring tests right there in my code.

## What if I want to keep my monitor configuration private?
You write your monitors in the same human-readable language, but restrict access to the file so only your monitoring provider can read it.

## Show me a sample monitors.txt already

A basic monitors.txt file for monitorstxt.org :

	Scenario: The home page should show the sample monitors.txt file
		When I visit http://monitorstxt.org
		Then I should see "The home page should show the sample monitors.txt file" within "body"

	Scenario: The monitorstxt.com domain should redirect to monitorstxt.org
		When I visit http://monitorstxt.com
		Then I should be redirected to http://monitorstxt.org

	Scenario: DNS should resolve the monitorstxt.org to the correct IP address
		When I lookup monitorstxt.org in DNS
		Then I should see the IP address: 1.2.3.4



## That looks a lot like a cucumber feature
monitors.txt needs to be flexible. Alternative formats could be supported, but right now I'm focused on making it readable, hence why 
I'm relying on cucumber/gherkin

## Feedback wanted
monitors.txt is a work in progress that I'd love your feedback on.
