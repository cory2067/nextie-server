# nextie.us

Have cool webapp ideas but not the resources to deploy them? As a resident of Next House, you can get free server space!

### What this is for

As an MIT student, you already have access to your [Athena locker](http://kb.mit.edu/confluence/pages/viewpage.action?pageId=3907090) where you can keep static webpages. You also have access to [scripts.mit.edu](http://scripts.mit.edu), which lets you do a bit more, like Python/php CGI scripts. However, if you wanted to host something like a node app, Flask app, or anything not supported by scripts, you'd be out of luck. But now, you can use the Next House server for whatever you want! But as we have limited resources, this is **not** a place for resource-intensive tasks.

### How does it work?

All services running on the nextie.us server are packaged as [Docker containers](https://www.docker.com/resources/what-container), to isolate them from each other. Each container can then expose port 80 and run a web server. All `*.nextie.us` hostnames all point to the same server IP. But depending on the hostname, requests are [reverse proxied](https://www.nginx.com/resources/glossary/reverse-proxy-server/) to the correct container.

### How do I get started?

[Fill out this application.](https://goo.gl/forms/9Lkrk56HXFymIcNF2)

You'll need to "dockerize" your app to make it run. This basically means adding a `Dockerfile`, which you can think of as a script that installs dependencies and launches your app. You can usually find nice Dockerfile guides/boilerplates online (e.g. google "dockerize flask app"). If you don't know what to do, you can contact me and we'll figure it out. If you need https support, I can generate certs. 

### Once approved, how do I deploy?

If your application sounds reasonable, you'll get a subdomain `xxx.nextie.us` and an ssh login `xxx@nextie.us`. There will be a directory `~/src` where you should clone your repo into. Users won't have `sudo` permissions and can't view each others' code. The server provides the following commands to interface with docker:

- `nextie publish`
  - Run `docker build` on the `~/src` directory and (re)starts the container.
- `nextie exec 'COMMAND'`
  - Execute a command in your container via `docker exec`
- `nextie logs`
  - View all output (`stdout` and `stderr`) in your container via `docker logs`
  
You should tell me any required Docker flags (like mounting volumes), and let me know if you want to use a custom URL. Feel free to request additional functionality or report potential flaws.

### Contact and support

For any questions and comments, please contact **nextie-help (at) mit (dot) edu**.

*- cor*
