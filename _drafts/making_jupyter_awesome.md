---
title: Making Jupyter Awesome 
---

[Jupyter](http://jupyter.org/) Notebooks are awesome. These days, they're one of the most popular tools in data science, especially if you're a python user (though I love it for R as well!). I love it for a bunch of reasons:
* It provides a great environment for quickly exploring data and prototyping ideas
* It makes it extremely easy to create reproducible analyses (this is especially important in a business setting, where stakeholders often need you to "refresh" your work with updated data or modified assumptions)
* It's a mechanism for sharing work with other data scientists, giving your peers a clear understanding of what you did, and what you were thinking when you did it
* It's a platform for working with data on a remote machine for tasks that simply would not be possible on your local computer
* It's highly customizable, with _excellent_ VIM keybinding support, completely customizable keyboard shortcuts, a number of available UI themes, and plenty of community-created plugins to make your life easier

It's not perfect though, which is to be expected since it's a completely free open-source tool. The main downsides I've found are:
* It doesn't pack the power of a full IDE -- for example, code completion exists, but for any sort of real engineering work, it's nowhere near the sophistication of something like PyCharm
* There is no local version; you _have to_ use it in a browser. It's worth noting that projects like [nteract](https://nteract.io/) and [Pineapple](https://nwhitehead.github.io/pineapple/) have sought to solve this. I haven't experimented with these enough to comment on them, but they look pretty cool
* Jupyter Notebooks can get _really_ messy and convoluted _really_ fast

With a few basic optimizations, we can resolve the last issue, and take advantage of some of the flexibility and customizability that Jupyter has to offer. Below I'll go through a few of my favorite tweaks and tricks for making Jupyter an even more awesome computing renvironment for data science. 