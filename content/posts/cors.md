---
author: "Kirti Bhardwaj"
date: 2023-05-11
linktitle: cors
prev: /posts/building-site-with-hugo
title: Introduction To Cross Origin Resource Sharing
weight: 10

---

## Introduction
A user agent makes a CORS request when it requests resource from a different domain, protocol or port. It is restricted on most browsers for security reasons, XMLHttpRequest and the Fetch API both follow [same origin policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)


***Same Origin Policy***

There is no single same origin policy.However, let us try to define some basics:

**What is Origin ?**
	</br>
	</br>
	According to [RFC 6454](https://tools.ietf.org/html/rfc6454) user-agents group URIs together into protection domains called **origin**.
	</br>
	Two URIs are part of **same origin** if they have **same scheme, host and port**.
	</br>
	For example, these urls will be treated as same origin: 

		http://example.com,  
		http://example.com:80,  
		http://example.com/path/file,  

Whereas, these will be different origin:

		http://example.com/
		http://example.com:8080/
		http://www.example.com/
		https://example.com:80/
		https://example.com/
		http://example.org/
		http://kirtib.com/


**What is Authority?**
	</br>
	</br>
	Even though we are digressing from the topic here but, authority is a good concept to understand. 
	Not every resource in an origin carries same authority (security). 
	</br>
	User-agents determine how much authority to grant a resource by examining its **media type** [mime-type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) and web applications can limit content's authority by restricting its media type.
	</br>
	For example, images have no authority but, html document has full authority of its origin.So,serving images is less risky then serving content with media-type 'text/html'.
	</br>
	</br>
	**Note: =>**
	If you add untrusted content in your web application, you can risk leaking origin's authority to untrusted content [Cross-side-scripting](https://en.wikipedia.org/wiki/Cross-site_scripting)

***Policy***
	</br>
	In general, user-agents isolate different origins and permit controlled communication between origins.This way a malicious website is not able to access content of a website you are logged into in a different tab. 
	</br>
	This StackExchange response explains it much better [Why is the same origin policy so important?](https://security.stackexchange.com/questions/8264/why-is-the-same-origin-policy-so-important)


Now, that we have a better understanding of same origin policy, we can move on to handling cross-origin-request.

## Cross-Origin Resource Access

Same-origin policy handles interactions between two origins, we can divide it into three categories:

* Writes: 
	* Usually allowed. Example: links, redirects. 
	* To block: CSRF token
* Embeds: 
	* Usually allowed. 
	* To block: Ensure resource can not be interpreted as embeddable.Content-Type header is not respected mostly, can also use CSRF token.
* Reads: 
	* Usually not allowed.
	* To block: Make a resource not embeddable

***Resources which may be embedded cross-origin***

* \<script></script> tag.
* \<link />, requires a content-type header.
* \<img>
* \<video></video> and \<audio></audio>.
* \<object></object>, \<embed> & \<applet></applet>.
*  Fonts with @font-face. 
* \<frame></frame>& \<iframe></iframe>. X-Frame-Options header can be used to disallow


We use CORS to allow cross-origin access.


***Practical Uses Of CORS***

 * External Stylesheets
 * Web fonts
 * Images
 * Public Apis
 * If your frontend application is running on a different port from backend server
 * Any external resources really.


## Cross Origin Resource Sharing (CORS)

Enabling CORS requires coordination between both the server and client.

**Cross Origin Request Algorithm Parameters**

Algorithm takes following params:

* Request Url => Url 
* Request Method => Method for request, default value is GET
* Author Request Headers => Headers set by authors, default is empty
* Request Entity Body => default is missing
* Source Origin => Origin of request
* Referrer Source => Determines referer header
* Manual Redirect Flag => Set when redirects are *not* to be followed automatically
* Omit Credentials Flag => Set when user credentials are to be *excluded* in request and cookies are to be ignored in response
* Force Preflight Flag => When preflight request is required


**Types**

1. **Simple CORS Requests**
	Simple CORS request are HTTP requests that include  `Origin` header.
	These request do no trigger preflight.There are a few conditions a request has to make to be classified as simple request:
	1. Allowed methods: GET, POST, HEAD
	2. Allowed values for Content-Type headers are:
		application/x-www-form-urlencoded; multipart/form-data and text/plain
	3. Only headers that can be manually set; apart from those set automatically by user-agent; are:
		[CORS Safelisted Request Headers](https://fetch.spec.whatwg.org/#cors-safelisted-request-header)
	4. No ReadableStream object is used in the request
	5. No event listeners are registered on any XMLHttpRequestUpload object used in the request


2. **Preflighted CORS Requests**

	These request send an option method to check if the actual resource is safe to send and checks if CORS protocol is understood. It includes `OPTIONS` method and includes `Access-Control-Request-Method`  and `Access-Control-Request-Headers`  headers.

	![Preflighted CORS](/images/preflighted-cors.png) 
	
	A request is preflighted if any of the below conditions are true:
	1. Methods: PUT, DELETE, CONNECT,OPTIONS,TRACE, PATCH
	2. Apart for user-agent headers it includes any headers other than safelisted request headers, defined above.These can be:
	   Accept, Accept-Language, Content-Language, Content-Type, Last-Event-ID etc.
	3. If Content-Type header has values other than above mentioned ones
	4. ReadableStream object is used in the request
	5. Event listeners are registered on any XMLHttpRequestUpload object used in the request

## About The Headers

Headers allow clients and servers to pass additional information along with the request or response. Syntax for a header is:

	Header Name : Header Value

Header Name is case-insensitve, value is a byte-sequence which has no leading (ignored) or trailing HTTP whitespace bytes and contains no 0x00, 0x0A or 0x0D bytes.


**1. Request Headers**
	</br>
	These are the http headers clients may set while making CORS request. These are automatically set by browser.

* Origin :
	</br>
	Info: Indicates the origin of request. This header is always set.Can be an empty string (useful if source is a data URL).Includes:

			Scheme: Protocol that is used e.g. HTTP or HTTPS
			Hostname: Domain name of the server or ip
			Port: TCP port on which server is listening. Default is 80.
	Set By: Browser 

	Example: </br>

		Origin: https://kirtib.com

* Access-Control-Request-Method:
	</br>
	Info: Used during preflight request to tell server what HTTP method will be used by the next request.Used because preflight request is always OPTIONS.Includes:
		HTTP request methods for ex. 'GET', 'POST'
	Set By: Browser

	Example:</br>

		Access-Control-Request-Method: POST

* Access-Control-Request-Headers:

	Info:Used during preflight to tell server what headers will be used by next request.Includes:

		List of HTTP headers included in the request, separated by commas.
	Set By: Browser

	Example:

		Access-Control-Request-Headers: X-PINGOTHER, Content-Type

	![request header example](/images/headers-request.png) 	

**2. Response Headers**
</br>
These headers are sent back by server for CORS requests.

* Access-Control-Allow-Origin: 

	Info: Indicates if the origin is allowed to access the resource.For requests without credentials, server may specify star (wildcard) thus, allowing any origin access to the resource

	Example:

			Access-Control-Allow-Origin: * 					[To allow access to any resource]
			Access-Control-Allow-Origin: https://kirtib.com [To allow access to https://kirtib.com]


	For example 2 where server specifies an origin host it must also include Origin in Vary response header to indicate that the responses will differ based on the value of Origin header.
		
	Example: 

			Access-Control-Allow-Origin: https://kirtib.com
			Vary: Origin

* Access-Control-Expose-Headers:

	Info: It indicates which headers can be exposed as part of response.That is, if you want a client to be able to access headers other than simple response headers that are exposed by default.Includes:

		A list of exposed headers which consist header names that are exposed and open to use.

	Example:
		
		Access-Control-Expose-Headers: Content-Length, Custom-header

	**Note: =>**

		Simple response headers are headers that have been safelisted also called CORS-safelisted-response-header and are not filtered when response is processed by CORS
		
		Simple response headers that are exposed by default are:
		    Cache-Control
		    Content-Language
		    Content-Type
		    Expires
		    Last-Modified
		    Pragma

	More about safelisted headers below.

* Access-Control-Max-Age:
	
	Info: Defines maximum number of seconds the result of preflight request can be cached. This information is contained in Access-Control-Allow-Methods and Access-Control-Allow-Headers. If value returned is -1, it will disable caching and forces a preflight OPTIONS check for all calls. Different browsers cap this value at different levels, some even specify a default value.

	Example:

		Access-Control-Max-Age: 86400

	(Caches for 24 hours)


* Access-Control-Allow-Credentials:
	
	Info: Tells whether the response can be shared when request's credential mode is 'include'.If returned as a response to preflight req, it tells if actual request can be made using credentials (For preflight, request's credential mode is always 'omit'). Credentials must be set on both sides for CORS to succeed.

	*Credentials can be cookies, authorization headers or TLS client certificates.*
	
	Example:

		Access-Control-Allow-Credentials: true
	
	With XHR:

		let xhr = new XMLHttpRequest();
		xhr.open('GET','http://kirtib.com', true);
		xhr.withCredentials = true;
		xhr.send(null);
	
	With Fetch:

		fetch(url, {credentials: 'include'});

* Access-Control-Allow-Methods:

	Info: Specifies which method/s are allowed when accessing resource in response to preflight request.

	Example:

		Access-Control-Allow-Methods: POST, GET, PATCH

* Access-Control-Allow-Headers:

	Info: Used in response to preflight request and indicates which HTTP headers (apart from simple headers) can be used during actual request.

	Required if `Access-Control-Request-Headers` header is present in request.

	Example:

			Access-Control-Allow-Headers: Custom-Header


**3. CORS-safelisted-request-headers**

These are headers whose name is byte-case-insensitive match for any one of:
	
	Accept,
	Accept-Language,
	Content-Language,
	Content-Type

and value has a MIME type that is `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain` 

or name is byte-case-insensitive match for any one of:

    DPR
    Downlink
    Save-Data
    Viewport-Width
    Width 

and value is not failure.

**4. CORS-safelisted-response-headers**

A response gets CORS-exposed-header-name list by extracting values from `Access-Control-Expose-Headers`. Given such a list this header name is byte-case-insensitive match for one of:

	Cache-Control
	Content-Language
	Content-Length
	Content-Type
	Expires
	Last-Modified
	Pragma 

any value in list that is not  a forbidden-response-header-name.

**5. Forbidden-response-header-name**

Header name which is byte-case-insensitive match for:

    Set-Cookie
    Set-Cookie2 

**6. Forbidden-header-name**

Header name which matches one of:
	
    Accept-Charset
    Accept-Encoding
    Access-Control-Request-Headers
    Access-Control-Request-Method
    Connection
    Content-Length
    Cookie
    Cookie2
    Date
    DNT
    Expect
    Host
    Keep-Alive
    Origin
    Referer
    TE
    Trailer
    Transfer-Encoding
    Upgrade
    Via 

or a header name that starts with byte-case-insensitive match for `Proxy-` or `Sec-`


More about CORS and credentials in the next post.


### Attribution


You can read more about it here:

* [Stack OverFlow](https://stackoverflow.com/questions/10636611/how-does-access-control-allow-origin-header-work)
* [Stack OverFlow](https://stackoverflow.com/questions/13400594/understanding-xmlhttprequest-over-cors-responsetext/13400954#13400954)
* [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)
* [Fetch Spec](https://fetch.spec.whatwg.org/)
* [HTML5Rocks](https://www.html5rocks.com/en/tutorials/cors/)
* [W3 Documentations](https://www.w3.org/TR/cors)
