---
author: "Kirti Bhardwaj"
date: 2018-05-11
linktitle: Intro-cors
prev: /posts/building-site-with-hugo
title: Introduction To Cross Origin Request Sharing
weight: 10

---

## Introduction


A user agent makes a CORS request when it requests resource from a different domain, protocol or port. It is restricted on most browsers for security reasons, XMLHttpRequest and the Fetch API both follow [same origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)

Enabling CORS requires coordination between both the server and client.

## Practical Uses Of CORS

 * External Stylesheets
 * Web fonts
 * Images

 Any external resources really.


## Types

**1) Simple CORS Requests**
	These request do no trigger preflight.There are a few conditions a request has to make to be classified as simple request:
	A) Allowed methods: GET, POST, HEAD
	B) Allowed values for Content-Type headers are:
		application/x-www-form-urlencoded; multipart/form-data and text/plain
	C) Only headers that can be manually set; apart from those set automatically by user-agent; are:
		[CORS Safelisted Request Headers](https://fetch.spec.whatwg.org/#cors-safelisted-request-header)
	D) No ReadableStream object is used in the request
	E) No event listeners are registered on any XMLHttpRequestUpload object used in the request


** 2) Preflighted CORS Requests **
	These request send an option method to check if the actual resource is safe to send.
	```
		 HTTP OPTIONS method is used to describe communication option 
	```


