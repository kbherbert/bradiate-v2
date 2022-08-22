---
title: Test localhost from any device on your LAN using Node
publishDate: 24 Dec 2019
description: 
---

Have you ever been developing a site locally and wanted to test your work on all of your devices? For instance, I am working on a couple of responsive Node.js apps on my laptop, but I wanted to be able to run those apps on my tablet or phone connected over wifi to my local network. So after a little research and pulling together some resources, I was able to get it working. The following describes how to get it setup, assuming you are familiar with Node.js and how to setup a basic app with [Express](https://expressjs.com).

First of all, for the machine that is acting as your Node server, make the following changes to `.listen()` in your core app file:

```js
// familiar code to start our server
server.listen(port, host);
});
```

The key here is setting your host to `0.0.0.0`. Don’t ask me why this works, but it does. You can supplement that with whatever port you choose. This is helpful if you are running multiple Node instances that map to different ports. My configuration looks like this:

```js
// start our server
server.listen(8124, 0.0.0.0);
});
```

So, on your server you can simply paste in the usual: http://localhost:8124. Assuming you have started your Node server, this should spin up your site.

To hit the server and view your site from any other device connected to your local network, simply type in your server machine’s IP address and port. Mine looks like this: http://192.168.1.65:8124.

That’s it!
