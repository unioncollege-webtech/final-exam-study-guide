# Final Exam Study Guide

The final exam in Web Technologies covers basic JavaScript language features as well as important <abbr title="HyperText Transfer Protocol">HTTP</abbr> topics such as methods, status codes, and headers.

## HyperText Transfer Protocol

<abbr title="HyperText Transfer Protocol">HTTP</abbr> is an *application level* protocol for communication between a user-agent (typically a browser) and a server. From the [HTTP 1.1 Specification](http://www.w3.org/Protocols/rfc2616/rfc2616-sec1.html#sec1.4):

> The HTTP protocol is a request/response protocol. A client sends a request to the server in the form of a [request method](#http-methods), URI, and protocol version, followed by a MIME-like message containing request modifiers, client information, and possible body content over a connection with a server. The server responds with a status line, including the message's protocol version and a [success or error code](#http-status-codes), followed by a MIME-like message containing server information, entity metainformation, and possible entity-body content. The relationship between HTTP and MIME is described in appendix 19.4.


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

#### Safe and Idempotent Methods

##### Safe Methods

GET and HEAD methods are considered "safe", meaning they SHOULD NOT have the significance of taking an action other than retrieval. GET and HEAD requests should not alter the resource being requested.

##### Idempotent Methods

The methods GET, HEAD, PUT and DELETE are considered "idempotent", meaning multiple identical requests for the same resource should have the same side-effects as a single request for that resource. POST methods are NOT expected to be idempotent.


### [HTTP Status Codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10)

HTTP statuses indicate the result of the attempt to understand and satisfy the request. The status consists of a Status-Code and a short textual description known as the Reason-Phrase. The Status-Code is a 3-digit integer. The first digit of the Status-Code defines the class of response. The last two digits do not have any categorization role. There are 5 values for the first digit:

- 1xx: Informational - Request received, continuing process
- 2xx: Success - The action was successfully received,
  understood, and accepted
- 3xx: Redirection - Further action must be taken in order to
  complete the request
- 4xx: Client Error - The request contains bad syntax or cannot
  be fulfilled
- 5xx: Server Error - The server failed to fulfill an apparently
  valid request

#### [100 Continue](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.1.1)

The client SHOULD continue with its request. This interim response is used to inform the client that the initial part of the request has been received and has not yet been rejected by the server. The client SHOULD continue by sending the remainder of the request or, if the request has already been completed, ignore this response. 

#### [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1)

The request has succeeded. The information returned with the response is dependent on the method used in the request

#### [301 Moved Permanently](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.2)

The requested resource has been assigned a new permanent URI (identified by the Location field in the response) and any future references to this resource should use the new URI. This response is cacheable unless indicated otherwise.

#### [302 Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.2)

The requested resource resides temporarily under a different URI. Since the redirection might be altered on occasion, the client SHOULD continue to use the Request-URI for future requests. This response is only cacheable if indicated by a Cache-Control or Expires header field.

#### [304 Not Modified](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.3.5)

If the client has performed a conditional GET request and access is allowed, but the document has not been modified, the server SHOULD respond with this status code. The 304 response MUST NOT contain a message-body, and thus is always terminated by the first empty line after the header fields.

#### [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

The request could not be understood by the server due to malformed syntax. The client SHOULD NOT repeat the request without modifications.

#### [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2)

The request requires user authentication.

#### [403 Forbidden](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.4)

The server understood the request, but is refusing to fulfill it. Authorization will not help and the request SHOULD NOT be repeated.

#### [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5)

The server has not found anything matching the Request-URI. No indication is given of whether the condition is temporary or permanent.

#### [410 Gone](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11)

The requested resource is no longer available at the server and no forwarding address is known. This condition is expected to be considered permanent.

#### [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1)

The server encountered an unexpected condition which prevented it from fulfilling the request.

#### [503 Service Unavailable](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.4)

The server is currently unable to handle the request due to a temporary overloading or maintenance of the server. 


### Message Headers

[HTTP header fields](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14) consist of a name followed by a colon (":") and the field value. There are four different categories of header fields:

- **general**: have general applicability for both request and response messages, but which do not apply to the entity being transferred
- **request**: allow the client to pass additional information about the request, and about the client itself, to the server. These fields act as request modifiers, with semantics equivalent to the parameters on a programming language method invocation.
- **response**: allow the server to pass additional information about the response which cannot be placed in the Status- Line. These header fields give information about the server and about further access to the resource identified by the Request-URI.
- **entity**: define metainformation about the entity-body or, if no body is present, about the resource identified by the request.

