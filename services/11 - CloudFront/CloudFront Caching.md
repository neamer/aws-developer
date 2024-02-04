The caches live at each [[AWS Edge location]], therefore we have as many caches as we have edge locations.

CloudFront identifies each object in the cache using the **Cache Key**

## Cache Keys

A cache key is a unique identifier for every object in the cache. It consists of hostname + resource portion of the URL

![[Pasted image 20240125202250.png]]
*This is the basic setup for caching. If the cache contains a object with the same origin and resource, it will serve it. But if it is absent from the cache then it will have to get the object from the origin first.*

## Cache Policies

Sometimes, we will want more complicated cache keys if our content will vary based on HTTP headers, cookies or query strings. We accomplish that by **CloudFront Cache Policies.**

We can create our own policies or use Predefined managed policies

We can create custom cache policies based on:

**HTTP Headers** with the following options:
- None - Don't include any headers in the cache key (except default)
- Whitelist - Only specified headers are included in the cache key

**Cookies** with the following options:
- None - Don't include any cookies in the cache key
- Whitelist - Only include specified cookies in the cache key
- Include All-Except - Include all cookies except the specified list
- All - Include all cookies in the cache key

**Query Strings** with the following options:
- None - Don't include any query strings in the cache key
- Whitelist - Only include specified query strings in the cache key
- Include All-Except - Include all query strings except the specified list
- All - Include all query strings in the cache key

An important thing to remember is that All HTTP Headers, cookies and query strings that you include in the cache key **are automatically included in origin requests.**

We can control the TTL with the Cache-Control headers or the Expires header.

## Origin Request Policy

Specify values that you want to include in origin requests without including them in the Cache Key (no duplicated cached content)

You can include:
- HTTP Headers: None, Whitelist, All viewer headers options
- Cookies: None, Whitelist, All
- Query Strings: None, Whitelist, All

We also have the ability to add CloudFront HTTP headers and custom headers to an origin request that were not present in the viewer request


## Example: Cache Policy vs Origin Request Policy

![[Pasted image 20240125204152.png]]

*Here we want cache based on our origin, resource and a header called Authorization. But, our origin needs more information to function properly. Therefore, we will add the User-Agent and Authorization headers, the session_id cookie and the ref query string to the origin request.*