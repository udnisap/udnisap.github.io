---
layout: post
section-type: post
title: Node REPL Experiments
tags: 
 - javascript
 - debugging
 - learning
 - hacks
---

I was hacking around the repl in node today. Basically REPL is Read Evaluate Print Loop. 
You run a command, it evaluates and print the results.

You can get it when you run `node` on the console. You can import stuff with `require` or built in modules with just the name on the promt

There are other variations of the REPL which built on top of that. Noticable mentions such as [repl-promised] which simply treat promise as part of the print cycle.
Which is not much of implementation but really cool. If you evaluvate a promise it will resolve and print the results.

I was specially interested in this because you can have your own `repl` programatically with node.

<pre><code data-trim class="js">
var repl = require('repl');
repl.start();
</code></pre>

Scary things about the repl is, it is not documented well. The documentation says
> On tab completion - eval will be called with .scope as an input string. It is expected to return an array of scope names to be used for the auto-completion.

but what it actually does is it calls `eval` when there is a `.`. check [repl issue] [repl source on github]
> means that if an object in the scope is in the promt with an ending . and user press on tab, eval is called with the object without the .

I was able hack in using following code and figure out what is going on inside.
<pre><code data-trim class="js">
var _ = require('lodash');
var repl = require('repl');

var replServer = repl.start({});
replServer.eval = _.wrap(replServer.eval, function(eval, cmd, context, filename, callback) {
    console.warn('eval with:', arguments);
    arguments[4] = _.wrap(callback, function(resultCallback){
        console.warn('result callbackdata:', arguments);
        resultCallback.apply(this, Array.prototype.slice.call(arguments, 1));
    });
    eval.apply(this, Array.prototype.slice.call(arguments, 1));
});
</code></pre>



[repl-promised]: https://github.com/tlrobinson/node-repl-promised
[repl-documentation]: https://nodejs.org/api/repl.html
[repl source on github]: https://github.com/nodejs/node/blob/v5.x/lib/repl.js
[repl issue]: https://github.com/nodejs/node/issues/3674#issuecomment-159606212