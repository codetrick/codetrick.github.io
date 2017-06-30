---
layout: post
title:  "DOI Resolver Plugin for Spotlight"
date: 2017-06-29 20:27 -0800
last_modified_at: 2017-06-30
published: true
categories: programming
---

As a graduate student having to read academic papers on a regular basis, frequently have I encountered references to journal articles in the form of DOI ([digital object identifiers][wiki_doi]). Quite often they don't come in hyperlink form, so it is annoying to actually access the paper by first copying the doi, then going to the [doi website][doi], pasting the doi into their tiny query box and clicking `submit`, being redirected to the journal page on whatever publisher's site, and finally being able to download the paper or hitting a paywall (which is when [Sci-Hub][scihub] comes to rescue...). 

I have long wanted to change that. 

<!--more-->

The first idea that comes to mind is to write a browser plugin that takes the standard doi format (like `doi:10.1000/182`) in the address bar and spits out whatever website [doi.org][doi] gives you. I thought, ok, it should *not* be so hard since these browsers already take urls with things like `https:` or `ftp:`. It then turns out that browsers are really not that configurable. Granted that you could add buttons to the toolbar, access and modify page contents with javascript, these are unfortunately almost all you can do in a browser plugin. There does not seem to be an easy way of dymanically processing what is requested in the address bar and redirecting the user to another page. [^note]

I then realized, writing a plugin for [Spotlight][wiki_spotlight] might be a better idea. For those who don't use MacOS, Spotlight is a feature in MacOS that does system-wide searches of apps, files, calendar events, emails, etc. It can be conveniently called out via the (default) keyboard shortcut `⌘-Space`, so it would be even simpler to use than a browser plugin, for which you would have to open up the browser first! However, one question remains: given how Apple dislikes software configurability (a common thing among most commercial softwares), is it even possible to do that?

The answer turns out to be *yes*. Of course there's no official API for Spotlight, but clever people have found a way to hack it! [Flashlight][flashlight] basically turns Spotlight into an open platform for doing anything you could imagine with it. I should note that the original Spotlight repository is no longer being maintained, and it does not work on El Capitan and Sierra. [A fork by w0lfschild][flashlight_fork] however is in active development and supports the latest MacOS versions. I could then have Flashlight handle the pattern matching, then simply provide the url link corresponding to the doi string. Better still, the code will be written in python!

After struggling a bit with Apple's [System Integrity Protection][wiki_sip], Flashlight is installed on my computer. Writing the script is easier than I could have imagined. Basically, all plugins are stored in `~/Library/FlashlightPlugins`, where each plugin (*aka* its descriptive files and the python script) resides in folders named `xxx.bundle`. The required files are as few as three: `info.json` defines the name and other attributes of the plugin, `examples.txt` has the string patterns that Flashlight will have to match, and `plugin.py` contains the functions Flashlight will call when patterns are matched. For a more detailed walkthrough for creating a Flashlight plugin, I recommend reading [this article][plugin_example] on its wiki. 

I then set out to write the plugin. The `examples.txt` file is as simple as two lines:

{% gist codetrick/c746ad7c3f3088b2301605ff6dbc4378 %}

This basically asks Flashlight to match any queries that look like `doi:10.1000/182` or `doi␣10.1103/PhysRev.106.162`, and then pass the matched text as the value to the key `'~name'` in a python dictionary object to the function `results(fields, original_query)` defined in `plugin.py`. The full script looks like this:

{% gist codetrick/0f766aa7338eb3e4c5a9b5c7dccefbc8 %}

As you can see, I generated the url for doi query, and have that displayed as html in the Spotlight window. When the user presses `Enter`, the function `run()` will be called with arguments returned by the `"run_args"` value of the `results()` function. Here I simply make a system call to open up the default browser to access the given url. It is as **simple** as that. 

Finally, you'll need an `info.json` file to tell Flashlight that this plugin exists. 

{% gist codetrick/a87cf06afeb88b1188e7bf4f9a71a9f0 %}

Now this doi resolver plugin is good to go! Look at this nice screenshot:

![DOI resolver screenshot]({{ site.url }}/assets/2017/06/doi_resolver_screenshot.png)

[^note]: [This DOI resolver](http://manumitting.com/tools/OpenDOI/) works with links outside of browsers, but does not work for requests initiated from the browser address bar. 

[doi]: https://doi.org
[wiki_spotlight]: https://en.wikipedia.org/wiki/Spotlight_(software)
[wiki_doi]: https://en.wikipedia.org/wiki/Digital_object_identifier
[scihub]: http://sci-hub.org
[flashlight]: http://flashlight.nateparrott.com
[flashlight_fork]: https://github.com/w0lfschild/Flashlight
[wiki_sip]: https://en.wikipedia.org/wiki/System_Integrity_Protection
[plugin_example]: https://github.com/nate-parrott/Flashlight/wiki/Creating-a-Plugin
