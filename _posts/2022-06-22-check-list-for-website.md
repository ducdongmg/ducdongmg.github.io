---
layout: single
title: "checklist cho website (dành cho developer)"
desc: "some description..."
keywords: "aaa, bbb"
categories: [aaa]
tag: [aaa, bbb]
---

# Web site checklist - for developers

There is a rich landscape of tools, frameworks and CMSes that greatly increase your productivity when building a web site. So when a path is selected, a design is implemented - there are just a few more things to consider to finalize your great accomplishment.

☑️ images should be minimized and delivered in best possible format (webp)  
☑️ images should be resized to match actual size and be lazy loaded  
☑️ make sure site is cached in best way  
☑️ server should serve http/2 (or http/3)  
☑️ add http caching so that files are cached in the browser  
☑️ sitemap should exist - and added to Google Search console  
☑️ robot should be able to crawl site  
☑️ meta description should exist on pages  
☑️ links and buttons should be clickable without mouse  
☑️ buttons with no text should have aria-label  
☑️ header-tags should be in order  
☑️ symantic html with main, nav, section and so on  
☑️ images have describing alt texts  
☑️ user should be able to tab through all interactive elements  
☑️ input fields should have labels  
☑️ make sure cache (including JavaScript and CSS files) is invalidated on deploy or content update  
☑️ if there is an existing site that are being updated, add redirects from old URLs to new  
☑️ analytics should be implemented  
☑️ no cookies should be saved before user consent  
☑️ sharing in social media should include editable title, description and image  
☑️ browsers used by the majority or your users should be supported and tested  
☑️ created 404 page  
☑️ add a descriptive readme file - another developer should easily be able to get the project up and running with the information  
☑️ branching workflow in git should be documented in readme file  
☑️ any environment specific settings should exist in a .env file (an .env.example file should be added to git)  
☑️ use addons/plugins/extensions that debug memory and database usage locally  
☑️ add error reporting for frontend and backend in production  
☑️ document any password or key in a password manager  
☑️ linting of the code should be configured and forced by other developers (though git workflows or deployment)

Cool, now we are done!

<div style="text-align: right">andreasbergqvist <a href="https://dev.to/andreasbergqvist/web-site-checklist-for-developers-11ff">dev.to</a></div>
