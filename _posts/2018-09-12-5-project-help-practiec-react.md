---
layout: single
title:  "5 Principles that will make you a SOLID JavaScript Developer"
desc: "5 Principles that will make you a SOLID JavaScript Developer"
excerpt: "5 Principles that will make you a SOLID JavaScript Developer"
keywords: "javascript, js, solid"
categories: [javascript]
tag: [javascript]
---

![5 Projects to Help You Practice React](https://daveceddia.com/images/react-practice-projects.png)

If you’re in the middle of trying to learn React, you have probably run into the “the gap.”

You have a handle on the basics: components, props, state. You’ve done a tutorial or two, and probably built a few To Do apps. Though your skills aren’t _quite_ at the level of building a real app yet, you know enough that building more To Do apps won’t take you any further.

5 React Project Ideas
---------------------

In this post I’ll show you 5 projects that will be fun to build, stretch your abilities a bit, and do not involve any todos.

The best thing you can do at this stage is to choose _simple_ and _small_ apps to build. Aim for quantity over quality. (here are some more ideas on [how to practice React](/learning-react-start-small))

### Tooling

I suggest using [Create React App](https://github.com/facebookincubator/create-react-app) to bootstrap these projects.

Social Card
-----------

We’ll start off with an easy one. This is more of a component than a full-blown app, but it’s a good place to start.

![social card](https://daveceddia.com/images/social-card.png)

Variations of this UI can be found all over the web – [Twitter](https://twitter.com), Facebook, Pinterest, [Airbnb](https://www.airbnb.com/), [Redfin](https://www.redfin.com/), and so on – and it serves as a solid building block for the sort of app where you want to display an image + some data.

It’s also good practice for breaking down a UI into React components.

Once you have a single `SocialCard` component rendering, try making a list of them with some fake data.

Weather App
-----------

Display a 5-day weather forecast, where each day shows the high and low temperatures, and an image for sunny/rainy/cloudy/snowy. Use fake, hard-coded data until you’ve got everything rendering correctly.

![Weather App](https://daveceddia.com/images/weather.png)

You might notice that the “days” look a lot like social cards…

For added practice, here are a few ways you could expand on the app:

*   Add the ability to click on a day, and see its hourly forecast. You can just maintain the current view in the top-level App state.
*   Add React Router to the project (`npm install react-router`) and follow the quick start guide [here](https://reacttraining.com/react-router/web/guides/quick-start) to add routes, such that `/` shows the 5-day forecast, and `/[name-of-day]` shows the hourly forecast for a particular day.
*   Sign up for a free API key from [Open Weather Map](https://openweathermap.org), fetch a real 5-day forecast, and feed that data into your app.
*   Want to get really fancy? Add a graphics library like [vx](https://vx-demo.now.sh/) and follow the examples [here](https://medium.com/vx-code/getting-started-with-vx-1756bb661410) to add a graph of the temperature over the course of a week or day.

You can see how this app starts off simple, but can be expanded at will to increase the challenge and the learning.

Hacker Hunt
-----------

Hacker Hunt is an aggregator of Hacker News stories with categories, but more importantly, it’s a good app to build for React practice.

[![Hacker Hunt screenshot](https://daveceddia.com/images/hackerhunt.png)](https://hackerhunt.co)

It has been said that all web apps are basically just lists. This app will give you some practice with lists of components that are a little more complicated than todos.

Use static data at first, and if you want a little more of a challenge, fetch stories from their API. From what I can glean from devtools, this is just a single route, [https://hackerhunt.co/api/daily/0](https://hackerhunt.co/api/daily/0), and you can replace the 0 with a different page number.

You could go a step further and replicate their routing structure with React Router.

Calculator
----------

![Calculator mockup](https://daveceddia.com/images/calculator.png)

You probably already know how these work. Add, subtract, multiply, divide… Clicking the numbers or the operations should perform the action.

For added challenge, respond to keyboard input too. You shouldn’t need to add an `<input>` element to make this work. If you do use an `<input>`, make it so that the user doesn’t need to focus the input control to type into it.

Spend a little time thinking about how the state will be represented. Do you need to store more than just the numbers on the display? When you type a new number, does it replace the display with that number, or append it to the end?

Add some [snapshot tests with Jest](/snapshot-testing-react-with-jest/) to test that the calculator works correctly.

Github Issues Page
------------------

Make a simplified version of Github’s Issues page. [Here’s an example](https://github.com/facebookincubator/create-react-app/issues). To keep the scope small, just focus on implementing the list of issues, and ignore the stuff in the header (search, filtering, stars, etc).

![Github issue list](https://daveceddia.com/images/github-issue-list.png)

Start by fetching open issues from [Github’s API](https://developer.github.com/v3/issues/) and displaying them in a list. You could use static data for this too.

Then add a pagination control to allow navigating through the entire list of issues. You might find it useful to add React Router too, so that you can navigate directly to a given page.

For added difficulty, implement the issue detail page too. Render the issue’s Markdown text and its comments using something like [react-markdown](https://github.com/rexxars/react-markdown).

![Github issue detail](https://daveceddia.com/images/github-issue-detail.png)

[Here is a working example](https://github.com/dceddia/github-issues-viewer) using React, Redux, and React Router that implements the features above plus a few more.

What Next?
----------

Hopefully I’ve given you some ideas for the kinds of things to build to help advance your React skills. For more along these lines, read about [Learning with Copywork](/learn-react-with-copywork/) and follow along to build a [metronome in React](/build-metronome-react/).

<div style="text-align: right">Theo <a href="https://daveceddia.com/react-practice-projects/">daveceddia</a></div>