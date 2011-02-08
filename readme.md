loaderator.js
==============
Rich HTML[5] pages often require a number of different resources to load before scripts can execute, especially for scripts that assume other scripts for definition.  Making sure resources are loaded in the right order can be difficult. Coders are sometimes tempted to load many scripts in the document header, which forces them to load synchronously (i.e. slowly) and delays page rendering.

**loaderator.js** is designed to make asynchronous loading scripts and media easy and fast, encouraging responsive user experiences.

Requirements
-------------
**loaderator.js** assumes it is running in a browser environment and may not work in a server or command-line program.  It has not been tested thoroughly, but it should at least work in recent versions of Firefox and Webkit.

No external libraries are required.

Features
--------
* Entirely event-based, never using `setTimeout` or `setInterval` (unless there is no other way)
* Event listeners for individual resources, groups of resources or for everything.
* Automatically detects/guesses the type of resource and best method of loading from file extension, unless specified
* handles the following methods of loading resources:
	- `<script>`: Add resource to document `head` as a script, allowing for Javascript and JSONP, even cross-domain
	- *Cascading Style Sheets*: Load external CSS file a `<link>` element
	- *AJAX*: 
	- *DOM Elements*: Creates the appropriate element based on resource type (images, audio, video, iframe), allowing for type-specific properties and methods (e.g. triggering load events for media on `canplay`, rather than waiting for the entire file)
	- *Fonts*: Wraps Google's [WebFont Loader](http://code.google.com/apis/webfonts/docs/webfont_loader.html). Great for fighting against the ["Flash of Unstyled Text"](http://paulirish.com/2009/fighting-the-font-face-fout/ "Fighting the @font-face FOUT")
* Checks for duplicates to avoid loading a given resource more than once (resolving relative URLs)
* Makes it unnecessary to load any scripts in `head`, even this one

Usage
--------
Coming soon...

License
-------
Coming soon.  Suggestions?

For now, use it non-commercially but don't distribute it without linking back here.  No warranties or guarantees.

Warning
--------
None of this has been extensively tested, and the interface is subject to change.  Please use it, test it and provide feedback, but be prepared to change your code when I change mine.

TO DO
--------
* Change `require` to `load` so it makes more sense. or maybe `push`?
* Add all CRUD features for all resources (create, remove, update, delete)
* Pass constructor parameters to `require`.
* Allow for addition of new `mode`s as plugins
* Enable specification of event type for media objects
* Add error handling for different types of failures, including retry-able (e.g. server timeout) and permanent (e.g. 404)
* Clean up resources array passed to event handlers
* Add `done` method that declares you're done adding resources and firing category and "all" event as soon as possible, even if all events have loaded already (maybe?)
* Accept an existing DOM element in place of a resource URL
* Make sure this works if it's loaded twice
* Clean up `LDR8R` and make it more elegant
* Separate out `console.log` calls into a debugging extension that can be turned on or off
* For *ajax* mode, allow for methods other than `GET` and additional parameters (headers, security credentials, `POST` data, etc.)
* Make sure we're not using `instanceof`.
* JS Lint this whole mess and make sure it minifies nicely
* Encapsulate it all in an anonymous function
* Build a test suite (little help, anyone?)