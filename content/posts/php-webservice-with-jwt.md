---
author: "Kirti Bhardwaj"
date: 2018-03-06
linktitle: Webservice-with-jwt-auth
prev: /posts/building-site-with-hugo
title: Creating a php web service for authorization
weight: 10

---

## Introduction

Recently, I needed to create a php webservice which any application could connect to and it would return you a JWT auth token authorizing you.
Here, I retrace my steps as well as share basic barebones code for such a webservice

## Url

First of all we needed a url we can hit so, I added a domain name to my /etc/hosts file

```
sudo vim /etc/hosts

Added below entry to the file

127.0.0.1       localhost kirti.test.com

```

So, now when we type kirti.test.com it will hit localhost, easy peasy. Now on to next step:

## Web Service

Now we create a folder auth, where we will store all our webservice related code.

This is how your folder structure will look like:

![Folder Structure](/images/folder.png) 

Now, first point of entrance is going to be ws.php [short for web service] whereas, custom.php will have the helper code/custom functions that we will write.We will create a config folder which will store our configurations etc.

Here is the code for web service.php

![Web service entry point](/images/wsphp.png) 

Now, your .htaccess file should be able to serve all the requests that come to it so, we will add

```
# Deny all the files
<Files ~ "^.*">
  Deny from all
</Files>

# Allow all from ws.php
<Files ws.php>
Allow from all
Satisfy any
</Files>

```

This to out .htaccess file. This essentially allows all requests for ws.php to be satisfied.

Now on to the important part, custom code, this has three parts:

1) Including all the config options:

```	require_once(config/constants.php);
```
2) Authorizing the username and password:

Here we write a custom function to authorize if username and password salt store for user matches the one user has entered as well as return a key if it matches.

3) Sending the JWT back to the querying code:

![Return JWT](/images/jwt.png) 


That's it. You can now hit the service with : 

```
"http://test.com/auth/ws.php?username=". $username . "&password=" . $password; 

```

Now you need to handle it on client side too, which entails another post.
