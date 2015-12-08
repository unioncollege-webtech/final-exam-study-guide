# Final Exam Study Guide

The final exam in Web Technologies covers basic JavaScript language features as well as important <abbr title="HyperText Transfer Protocol">HTTP</abbr> topics such as methods, status codes, and headers.

## HyperText Transfer Protocol

<abbr title="HyperText Transfer Protocol">HTTP</abbr> is an *application level* protocol for communication between a user-agent (typically a browser) and a server.

### HTTP Methods

HTTP defines several **Methods** which indicate the action to take for the specified resource. See the [Method Definitions](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9) in the HTTP 1.1 specification.

#### [OPTIONS](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.2)

The OPTIONS method represents a request for information about the communication options available on the request/response chain identified by the Request-URI. This method allows the client to determine the options and/or requirements associated with a resource, or the capabilities of a server, without implying a resource action or initiating a resource retrieval.

#### [GET](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3)

The GET method means retrieve whatever information (in the form of an entity) is identified by the Request-URI.

#### [HEAD](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.4)

The HEAD method is identical to GET except that the server MUST NOT return a message-body in the response. 

The metainformation contained in the HTTP headers in response to a HEAD request SHOULD be identical to the information sent in response to a GET request. This method can be used for obtaining metainformation about the entity implied by the request without transferring the entity-body itself. This method is often used for testing hypertext links for validity, accessibility, and recent modification.

#### [POST](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.5)

The POST method is used to request that the origin server accept the entity enclosed in the request as a new subordinate of the resource identified by the Request-URI. POST was originally designed to allow a uniform method to cover the following common functions:

- Posting a message to a bulletin board, newsgroup, mailing list, or similar group of articles;
- Providing a block of data, such as the result of submitting a form, to a data-handling process;
- Annotating or altering existing resources.

#### [PUT](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.5)

The PUT method requests that the enclosed entity be stored under the supplied Request-URI.

#### [DELETE](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.7)

The DELETE method requests that the origin server delete the resource identified by the Request-URI.

#### [PATCH](http://tools.ietf.org/html/rfc5789#section-2)

Specified in [RFC 5789](http://tools.ietf.org/html/rfc5789), the PATCH method requests that a set of changes described in the request entity be applied to the resource identified by the Request-URI.
