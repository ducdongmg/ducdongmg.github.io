---
layout: single
title:  "10 lời khuyên để trở thành Node Developer tốt hơn trong năm 2017"
desc: "10 lời khuyên để trở thành Node Developer tốt hơn trong năm 2017"
excerpt: "10 lời khuyên để trở thành Node Developer tốt hơn trong năm 2017"
keywords: "JavaScript, js, nodejs"
header:
  teaser: seed-to-giant.png
categories: [language]
tags: [JavaScript]
---
{% include toc %}

I started working with Node full-time in 2012 when I joined Storify. Since then, I have never looked back or felt that I missed Python, Ruby, Java or PHP — languages with which I had worked during my previous decade of web development.

Storify was an interesting job for me, because unlike many other companies, Storify ran (and maybe still does) everything on JavaScript. You see, most companies, especially large ones such as PayPal, Walmart, or Capital One, only use Node for certain parts of their stack. Usually they use it as an API gateway or an orchestration layer. That’s great. But for a software engineer, nothing compares with full immersion into a Node environment.

In this post I’ll outline ten tips to help you become a better Node developer in 2017. These tips come from me, who saw and learned them in the trenches, as well as people who have written the most popular Node and npm modules. Here’s what we’ll be covering:

Avoid complexity — Organize your code into the smallest chunks possible until they look too small and then make them even smaller.
Use asynchronous code — Avoid synchronous code like the plague.
Avoid blocking require — Put ALL your require statements at the top of the file because they are synchronous and will block the execution.
Know that require is cached — This could be a feature or a bug in your code.
Always check for errors — Errors are not footballs. Never throw errors and never skip the error check.
Use try…catch only in sync code — try...catch is useless for async code, plus V8 can’t optimize code in try...catch as well as plain code.
Return callbacks or use if … else — Just to be sure, return a callback to prevent execution from continuing.
Listen to the error events — Almost all Node classes/objects extend the event emitter (observer pattern) and emit the error event. Be sure to listen to that.
Know your npm — Install modules with -S or -D instead of --save or --save-dev
Use exact versions in package.json: npm stupidly adds a caret by default when you use -S, so get rid of them manually to lock the versions. Never trust semver in your apps, but do so in open-source modules.
Bonus — Use different dependencies. Put things your project needs only in development in devDependencies and then use npm i --production. The more un-required dependencies you have, the greater the risk of vulnerability.
So let’s bisect and take a look at each one of them individually. Shall we?

And don’t forget: as mentioned above, this is part one. You can find a further ten tips in part two.

### Avoid Complexity
Take a look at some of the modules written by Isaac Z. Schlueter, the creator of npm. For example, use-strict enforces JavaScript strict mode for modules, and it’s just three lines of code:

```js
var module = require('module')
module.wrapper[0] += '"use strict";'
Object.freeze(module.wrap)
```

So why avoid complexity? A famous phrase which originated in the US Navy according to one of the legends proclaims: KEEP IT SIMPLE STUPID (or is it “Keep it simple, stupid”?). That’s for a reason. The human brain can hold only five to seven items in its working memory at any one time. This is just a fact.

By keeping your code modularized into smaller parts, you and other developers can understand and reason about it better. You can also test it better. Consider this example,

```js
app.use(function(req, res, next) {
  if (req.session.admin === true) return next()
  else return next(new Error('Not authorized'))
}, function(req, res, next) {
  req.db = db
  next()
})
```

Or this code:

```js
const auth = require('./middleware/auth.js')
const db = require('./middleware/db.js')(db)

app.use(auth, db)
```

I’m sure most of you will prefer the second example, especially when the names are self-explanatory. Of course, when you write the code you might think that you understand how it works. Maybe you even want to show off how smart you are by chaining several methods together in one line. Please, code for the dumber version of you. Code for the you who hasn’t looked at this code for six months, or a tried or drunk version of you. If you write code at the peak of your mental capacity, then it will be harder for you to understand it later, not to even mention your colleagues who are not even familiar with the intricacies of the algorithm. Keeping things simple is especially true for Node which uses the asynchronous way.

And yes, there was the left-pad incident but that only affected projects dependent on the public registry and the replacement was published in 11 minutes. The benefits of going small far outweigh the downsides. Also, npm has changed its unpublish policy, and any serious project should be using a caching strategy or a private registry (as a temporary solution).

### Use Asynchronous Code
Synchronous code does have a (small) place in Node. It’s mostly for writing CLI commands or other scripts not related to web apps. Node developers mostly build web apps, hence they use async code to avoid blocking threads.

For example, this might be okay if we are just building a database script, and not a system to handle parallel/concurrent tasks:

```js
let data = fs.readFileSync('./acconts.json')
db.collection('accounts').insert(data, (results))=>{
  fs.writeFileSync('./accountIDs.json', results, ()=>{process.exit(1)})
})
```

But this would be better when building a web app:

```js
app.use('/seed/:name', (req, res) => {
  let data = fs.readFile(`./${req.params.name}.json`, ()=>{
    db.collection(req.params.name).insert(data, (results))=>{
      fs.writeFile(`./${req.params.name}IDs.json`, results, ()={res.status(201).send()})
    })
  })
})
```

The difference is whether you are writing concurrent (typically long running) or non-concurrent (short running) systems. As a rule of thumb, always write async code in Node.

### Avoid Blocking require
Node has a simple module loading system which uses the CommonJS module format. Its built-in require function is an easy way to include modules that exist in separate files. Unlike AMD/requirejs, the Node/CommonJS way of module loading is synchronous. The way require works is: you import what was exported in a module, or a file.

const react = require('react')
What most developers don’t know is that require is cached. So, as long as there are no drastic changes to the resolved filename (and in the case of npm modules there are none), then the code from the module will be executed and loaded into the variable just once (for that process). This is a nice optimization. However, even with caching, you are better off putting your require statements first. Consider this code which only loads the axios module on the route which actually uses it. The /connect route will be slower than needed because the module import is happening when the request is made:

```js
app.post('/connect', (req, res) => {
  const axios = require('axios')
  axios.post('/api/authorize', req.body.auth)
    .then((response)=>res.send(response))
})
```

A better, more performant way is to load the modules before the server is even defined, not in the route:

```js
const axios = require('axios')
const express = require('express')
app = express()
app.post('/connect', (req, res) => {
  axios.post('/api/authorize', req.body.auth)
    .then((response)=>res.send(response))
})
```

### Know That require Is Cached
I mentioned that require is cached in the previous section, but what’s interesting is that we can have code outside of the module.exports. For example,

```js
console.log('I will not be cached and only run once, the first time')

module.exports = () => {
  console.log('I will be cached and will run every time this module is invoked')
}
```
Knowing that some code might run only once, you can use this feature to your advantage.

### Always Check for Errors
Node is not Java. In Java, you throw errors because most of the time if there’s an error you don’t want the application to continue. In Java, you can handle multiple errors at a higher levels with a single try...catch.

Not so with Node. Since Node uses the event loop and executes asynchronously, any errors are separated from the context of any error handler (such as try...catch) when they occur. This is useless in Node:

```js
try {
  request.get('/accounts', (error, response)=>{
    data = JSON.parse(response)
  })
} catch(error) {
  // Will NOT be called
  console.error(error)
}
```

But try...catch still can be used in synchronous Node code. So this is a better refactoring of the previous snippet:

```js
request.get('/accounts', (error, response)=>{
  try {
    data = JSON.parse(response)
  } catch(error) {
    // Will be called
    console.error(error)
  }
})
```

If we cannot wrap the request call in a try...catch block, that leaves us with errors coming from request unhandled. Node developers solve this by providing you with error as a callback argument. Thus, you need to always manually handle the error in each and every callback. You do so by checking for an error (make sure it’s not null) and then either displaying the error message to the user or a client and logging it, or passing it back up the call stack by calling the callback with error (if you have the callback and another function up the call stack).

```js
request.get('/accounts', (error, response)=>{
  if (error) return console.error(error)
  try {
    data = JSON.parse(response)
  } catch(error) {
    console.error(error)
  }
})
```

A little trick you can use is the okay library. You can apply it like this to avoid manual error check on myriads of nested callbacks (Hello, callback hell).

```js
var ok = require('okay')

request.get('/accounts', ok(console.error, (response)=>{
  try {
    data = JSON.parse(response)
  } catch(error) {
    console.error(error)
  }
}))
```

### Return Callbacks or Use if … else
Node is concurrent. So it’s a feature which can turn into a bug if you are not careful. To be on the safe side terminate the execution with a return statement:

```js
let error = true
if (error) return callback(error)
console.log('I will never run - good.')
```

Avoid some unintended concurrency (and failures) due to mishandled control flow.

```js
let error = true
if (error) callback(error)
console.log('I will run. Not good!')
```

Just to be sure, return a callback to prevent execution from continuing.

### Listen to the error Events
Almost all Node classes/objects extend the event emitter (observer pattern) and emit the error event. This is an opportunity for developers to catch those pesky errors and handle them before they wreak havoc.

Make it a good habit to create event listeners for error by using .on():

```js
var req = http.request(options, (res) => {
  if (('' + res.statusCode).match(/^2\d\d$/)) {
    // Success, process response
  } else if (('' + res.statusCode).match(/^5\d\d$/))
    // Server error, not the same as req error. Req was ok.
  }
})

req.on('error', (error) => {
  // Can't even make a request: general error, e.g. ECONNRESET, ECONNREFUSED, HPE_INVALID_VERSION
  console.log(error)
})
```

### Know Your npm
Many Node and event front-end developers know that there is --save (for npm install) which will not only install a module but create an entry in package.json with the version of the module. Well, there’s also --save-dev, for devDependencies (stuff you don’t need in production). But did you know you can just use -S and -D instead of --save and --save-dev? Yes, you can.

And while you’re in the module installation mode, go ahead and remove those ^ signs which -S and -D will create for you. They are dangerous because they’ll allow npm install (or its shortcut npm i) to pull the latest minor (second digit in the semantic versioning) version from npm. For example, v6.1.0 to v6.2.0 is a minor release.

npm team believes in semver, but you should not. What I mean is that they put caret ^ because they trust open source developers to not introduce breaking changes in minor releases. No one sane should trust it. Lock your versions. Even better, use shrinkwrap: npm shrinkwrap which will create a new file with exact versions of dependencies of dependencies.

### Conclusion
This post was part one of two. We’ve already covered a lot of ground, from working with callbacks and asynchronous code, to checking for errors and locking down dependencies. I hope you’ve found something new or useful here. If you liked it, be sure to check out part two: 10 Node.js Best Practices: Enlightenment from the Node Gurus.

<div style="text-align: right">Theo <a href="https://www.sitepoint.com/10-tips-to-become-a-better-node-developer">sitepoint</a></div>