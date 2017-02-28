#Progressive Web Apps Training
This was a training session provided by Google Developers to teach companies how to use progressive web apps.
This course usually goes for three days, however we attended the course for two days. Where they covered a range of different topics, about how to think and structure building progressive web apps and how to also implement these techniques. The workshops were 40% hands on lab exercises.

## Contents
[Introduction to Progressive Web Apps](#introduction-to-progressive-web-apps)<br>
[New techniques for responsive design (with lab)](#New techniques for responsive design)<br>
[Working with Responsive Images (with lab)](#)<br>
[Introduction to Service Workers](#introduction-to-service-workers)<br>
[Adding offline support for an existing content site (with lab)](#)<br>
[Designing PWA support for dynamic sites & web apps](#)<br>
[Auditing an existing site with Lighthouse (with lab)](#lighthouse)<br>
[Using sw-toolbox and sw-precache to automate Service Worker creation (with lab)](#)<br>
[Deeper dive into core technologies (Promises, Fetch API, Cache API)](#)<br>
[Working with Indexed DB (with lab)](#)<br>
[Building apps that cache live data in the service worker](#)<br>
[Discoverability & Analytics](#)<br>

## Introduction to Progressive Web Apps
By definintion Progressive Web Apps are user experiences that have the reach of the web, and are:
- **Reliable** - Load instantly and never show the downasaur, even in uncertain network conditions.
- **Fast** - Respond quickly to user interactions with silky smooth animations and no janky scrolling.
- **Engaging** - Feel like a natural app on the device, with an immersive user experience.

This new level of of quality allows Progressive Web Apps to earn a place on the user's home screen.


## New techniques for responsive design


## Auditing an existing site with Lighthouse (with lab)
[**Get Lighthouse**](https://developers.google.com/web/tools/lighthouse/)<br>
Lighthouse is a tool for auditing an app for PWA features and checking your app meets a respectable bar for web performance under emulated mobile conditions.<br>
> Lighthouse can be run as a Chrome Extension, from the command line, or used programmatically as a Node module.


## App Shell
The app's shell is the minimal HTML, CSS, and JavaScript that is required to power the user interface. Its first load should be extremely quick and immediately cached, it should be loaded once over the network and then saved to the local device. Next time the user comes to the site on their device the files are loaded from their cache and start-up time should be extremely fast now.<br>
The shell architecture should separate the core application infrastructure and UI from the data. The shell is cached using a service worker, so that on future loads the app only has to retrieve the relevant data rather than reloading everything.

Designing your app using the shell allows you to focus on speed and gives you similar properties to native apps: instant loading and regular updates, all without the need of an app store.

> example of what the shell should be

<img src="../assets/pwa/app-shell.png" width="450px"/>

##### Design tips for a shell
First break the site down to its core components.
1. What needs to be on the screen immediately
2. Key UI components of the app
3. Which supporting resources are needed. For example images, JavaScript, styles, etc.

When designing a more complex app, content that isn't needed for the initial load can be requested later and then cached for future use.

## Introduction to Service Workers
A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction.<br>

It is a programmable network proxy, allowing you to control how network requests from your page are handled. –

##### Features <br>
Intercept network requests<br>
Requests caching<br>
Push notifications<br>
Background sync (proposed)<br>
Geo-fencing (proposed)

***Example of how to register your service worker***

```

navigator.serviceWorker.register('service-worker.js').then(function(registration) {
  console.log('registered!', registration)
});
```

It is important to put this file in the root of your site, so that it can act on any requests to your domain. For example if you put it in `/js/service-worker.js` then it would only be able to act on requests mad to `/js`

It's also important to wrap this with a check to see if the browser supports service workers, currently ios doesn't.

```
if ('serviceWorker' in navigator) {

}
```

**How to test if your service worker is there:**<br>
In Chrome you can do this by<br>
<span style="color:#745ABD">***opening DevTools -> Click on "Application" -> Check for registered ServiceWorker***.</span><br>
You should be able to find `service-worker.js` (or whatever you named your file).


After you've registered the service worker, the browser will now install it and activate it. <br>
The script will be installed in the user’s browser and it will live there even after the user has left your site.

When it's installed ***see the event handler below***, is when you should begin to cache your files.<br>
The cache can be accessed by: `caches.open(CACHE_NAME)`

You need to specify the name of the cache you want to use. This usually includes the version number, so you can use a new cache for the updated resources when you release a new version.

The method will return a promise, which resolves to the cache object. You can use this cache object to add the files you want to cache. The `addAll` method takes in an array of URLs, retrieves them, and adds the responses to the cache.

It's good to wrap the cache call with a Promise that resolves when everything you want to do in the install event is done. If not, the worker will be marked as installed and will be activated before it is ready. To do this put the caches.open chain into event.waitUntil:
```
self.addEventListener('install', event => {
  console.log('installed!', event);
  event.waitUntil(
    caches.open(CACHE_NAME)
    .then(function (cache) {
      //...
    })
  );
});
```

**How to test if your files are cached**<br>
<span style="color:#745ABD">***Open up DevTools -> Application tab -> Cache Storage***</span><br>
You should see that all the files in URLs list are in the CACHE_NAME (whatever you named it) cache.

***Example of event handlers***

```
self.addEventListener('install', event => {
  console.log('installed!', event);
});

self.addEventListener('activate', event => {
  console.log('activated!', event);
});

self.addEventListener('fetch', event => {
  console.log('fetched!', event.request.url, event);
});
```
