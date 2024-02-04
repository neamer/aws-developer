Signature Version 4 is used for signing HTTP requests to Amazon services.

# Authentication methods

You can express authentication information by using one of the following methods:

- HTTP Authorization header – Using the HTTP `Authorization` header is the most common method of authenticating an Amazon S3 request. All of the Amazon S3 REST operations (except for browser-based uploads using POST requests) require this header.  ![[Pasted image 20240117134357.png]]
- Query string parameters – You can use a query string to express a request entirely in a URL. In this case, you use query parameters to provide request information, including the authentication information. Because the request signature is part of the URL, this type of URL is often referred to as a presigned URL. You can use presigned URLs to embed clickable links, which can be valid for up to seven days, in HTML.  ![[Pasted image 20240117134432.png]]

