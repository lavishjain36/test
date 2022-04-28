# test

This document has been superseded. In 2014, RFC2616 was replaced by multiple RFCs (7230-7237). See IETF Documents for more information.

Network Working Group                                      R. Fielding
Request for Comments: 2616                                   UC Irvine
Obsoletes: 2068                                              J. Gettys
Category: Standards Track                                   Compaq/W3C
                                                              J. Mogul
                                                                Compaq
                                                            H. Frystyk
                                                               W3C/MIT
                                                           L. Masinter
                                                                 Xerox
                                                              P. Leach
                                                             Microsoft
                                                        T. Berners-Lee
                                                               W3C/MIT
                                                             June 1999
Hypertext Transfer Protocol -- HTTP/1.1
Status of this Memo
This document specifies an Internet standards track protocol for the Internet community, and requests discussion and suggestions for improvements. Please refer to the current edition of the "Internet Official Protocol Standards" (STD 1) for the standardization state and status of this protocol. Distribution of this memo is unlimited.

Copyright Notice
Copyright (C) The Internet Society (1999). All Rights Reserved.

Abstract
The Hypertext Transfer Protocol (HTTP) is an application-level protocol for distributed, collaborative, hypermedia information systems. It is a generic, stateless, protocol which can be used for many tasks beyond its use for hypertext, such as name servers and distributed object management systems, through extension of its request methods, error codes and headers [47]. A feature of HTTP is the typing and negotiation of data representation, allowing systems to be built independently of the data being transferred.

HTTP has been in use by the World-Wide Web global information initiative since 1990. This specification defines the protocol referred to as "HTTP/1.1", and is an update to RFC 2068 [33].

Table of Contents
Introduction ... 1
Purpose ... 1.1
Requirements ... 1.2
Terminology ... 1.3
Overall Operation ... 1.4
Notational Conventions and Generic Grammar ... 2
Augmented BNF ... 2.1
Basic Rules ... 2.2
Protocol Parameters ... 3
HTTP Version ... 3.1
Uniform Resource Identifiers ... 3.2
General Syntax ... 3.2.1
http URL ... 3.2.2
URI Comparison ... 3.2.3
Date/Time Formats ... 3.3
Full Date ... 3.3.1
Delta Seconds ... 3.3.2
Character Sets ... 3.4
Missing Charset ... 3.4.1
Content Codings ... 3.5
Transfer Codings ... 3.6
Chunked Transfer Coding ... 3.6.1
Media Types ... 3.7
Canonicalization and Text Defaults ... 3.7.1
Multipart Types ... 3.7.2
Product Tokens ... 3.8
Quality Values ... 3.9
Language Tags ... 3.10
Entity Tags ... 3.11
Range Units ... 3.12
HTTP Message ... 4
Message Types ... 4.1
Message Headers ... 4.2
Message Body ... 4.3
Message Length ... 4.4
General Header Fields ... 4.5
Request ... 5
Request-Line ... 5.1
Method ... 5.1.1
Request-URI ... 5.1.2
The Resource Identified by a Request ... 5.2
Request Header Fields ... 5.3
Response ... 6
Status-Line ... 6.1
Status Code and Reason Phrase ... 6.1.1
Response Header Fields ... 6.2
Entity ... 7
Entity Header Fields ... 7.1
Entity Body ... 7.2
Type ... 7.2.1
Entity Length ... 7.2.2
Connections ... 8
Persistent Connections ... 8.1
Purpose ... 8.1.1
Overall Operation ... 8.1.2
Proxy Servers ... 8.1.3
Practical Considerations ... 8.1.4
Message Transmission Requirements ... 8.2
Persistent Connections and Flow Control ... 8.2.1
Monitoring Connections for Error Status Messages ... 8.2.2
Use of the 100 (Continue) Status ... 8.2.3
Client Behavior if Server Prematurely Closes Connection ... 8.2.4
Method Definitions ... 9
Safe and Idempotent Methods ... 9.1
Safe Methods ... 9.1.1
Idempotent Methods ... 9.1.2
OPTIONS ... 9.2
GET ... 9.3
HEAD ... 9.4
POST ... 9.5
PUT ... 9.6
DELETE ... 9.7
TRACE ... 9.8
CONNECT ... 9.9
Status Code Definitions ... 10
Informational 1xx ... 10.1
100 Continue ... 10.1.1
101 Switching Protocols ... 10.1.2
Successful 2xx ... 10.2
200 OK ... 10.2.1
201 Created ... 10.2.2
202 Accepted ... 10.2.3
203 Non-Authoritative Information ... 10.2.4
204 No Content ... 10.2.5
205 Reset Content ... 10.2.6
206 Partial Content ... 10.2.7
Redirection 3xx ... 10.3
300 Multiple Choices ... 10.3.1
301 Moved Permanently ... 10.3.2
302 Found ... 10.3.3
303 See Other ... 10.3.4
304 Not Modified ... 10.3.5
305 Use Proxy ... 10.3.6
306 (Unused) ... 10.3.7
307 Temporary Redirect ... 10.3.8
Client Error 4xx ... 10.4
400 Bad Request ... 10.4.1
401 Unauthorized ... 10.4.2
402 Payment Required ... 10.4.3
403 Forbidden ... 10.4.4
404 Not Found ... 10.4.5
405 Method Not Allowed ... 10.4.6
406 Not Acceptable ... 10.4.7
407 Proxy Authentication Required ... 10.4.8
408 Request Timeout ... 10.4.9
409 Conflict ... 10.4.10
410 Gone ... 10.4.11
411 Length Required ... 10.4.12
412 Precondition Failed ... 10.4.13
413 Request Entity Too Large ... 10.4.14
414 Request-URI Too Long ... 10.4.15
415 Unsupported Media Type ... 10.4.16
416 Requested Range Not Satisfiable ... 10.4.17
417 Expectation Failed ... 10.4.18
Server Error 5xx ... 10.5
500 Internal Server Error ... 10.5.1
501 Not Implemented ... 10.5.2
502 Bad Gateway ... 10.5.3
503 Service Unavailable ... 10.5.4
504 Gateway Timeout ... 10.5.5
505 HTTP Version Not Supported ... 10.5.6
Access Authentication ... 11
Content Negotiation ... 12
Server-driven Negotiation ... 12.1
Agent-driven Negotiation ... 12.2
Transparent Negotiation ... 12.3
Caching in HTTP ... 13
@@ missing
Cache Correctness ... 13.1.1
Warnings ... 13.1.2
Cache-control Mechanisms ... 13.1.3
Explicit User Agent Warnings ... 13.1.4
Exceptions to the Rules and Warnings ... 13.1.5
Client-controlled Behavior ... 13.1.6
Expiration Model ... 13.2
Server-Specified Expiration ... 13.2.1
Heuristic Expiration ... 13.2.2
Age Calculations ... 13.2.3
Expiration Calculations ... 13.2.4
Disambiguating Expiration Values ... 13.2.5
Disambiguating Multiple Responses ... 13.2.6
Validation Model ... 13.3
Last-Modified Dates ... 13.3.1
Entity Tag Cache Validators ... 13.3.2
Weak and Strong Validators ... 13.3.3
Rules for When to Use Entity Tags and Last-Modified Dates ... 13.3.4
Non-validating Conditionals ... 13.3.5
Response Cacheability ... 13.4
Constructing Responses From Caches ... 13.5
End-to-end and Hop-by-hop Headers ... 13.5.1
Non-modifiable Headers ... 13.5.2
Combining Headers ... 13.5.3
Combining Byte Ranges ... 13.5.4
Caching Negotiated Responses ... 13.6
Shared and Non-Shared Caches ... 13.7
Errors or Incomplete Response Cache Behavior ... 13.8
Side Effects of GET and HEAD ... 13.9
Invalidation After Updates or Deletions ... 13.10
Write-Through Mandatory ... 13.11
Cache Replacement ... 13.12
History Lists ... 13.13
Header Field Definitions ... 14
Accept ... 14.1
Accept-Charset ... 14.2
Accept-Encoding ... 14.3
Accept-Language ... 14.4
Accept-Ranges ... 14.5
Age ... 14.6
Allow ... 14.7
Authorization ... 14.8
Cache-Control ... 14.9
What is Cacheable ... 14.9.1
What May be Stored by Caches ... 14.9.2
Modifications of the Basic Expiration Mechanism ... 14.9.3
Cache Revalidation and Reload Controls ... 14.9.4
No-Transform Directive ... 14.9.5
Cache Control Extensions ... 14.9.6
Connection ... 14.10
Content-Encoding ... 14.11
Content-Language ... 14.12
Content-Length ... 14.13
Content-Location ... 14.14
Content-MD5 ... 14.15
Content-Range ... 14.16
Content-Type ... 14.17
Date ... 14.18
Clockless Origin Server Operation ... 14.18.1
ETag ... 14.19
Expect ... 14.20
Expires ... 14.21
From ... 14.22
Host ... 14.23
If-Match ... 14.24
If-Modified-Since ... 14.25
If-None-Match ... 14.26
If-Range ... 14.27
If-Unmodified-Since ... 14.28
Last-Modified ... 14.29
Location ... 14.30
Max-Forwards ... 14.31
Pragma ... 14.32
Proxy-Authenticate ... 14.33
Proxy-Authorization ... 14.34
Range ... 14.35
Byte Ranges ... 14.35.1
Range Retrieval Requests ... 14.35.2
Referer ... 14.36
Retry-After ... 14.37
Server ... 14.38
TE ... 14.39
Trailer ... 14.40
Transfer-Encoding ... 14.41
Upgrade ... 14.42
User-Agent ... 14.43
Vary ... 14.44
Via ... 14.45
Warning ... 14.46
WWW-Authenticate ... 14.47
Security Considerations ... 15
Personal Information ... 15.1
Abuse of Server Log Information ... 15.1.1
Transfer of Sensitive Information ... 15.1.2
Encoding Sensitive Information in URI's ... 15.1.3
Privacy Issues Connected to Accept Headers ... 15.1.4
Attacks Based On File and Path Names ... 15.2
DNS Spoofing ... 15.3
Location Headers and Spoofing ... 15.4
Content-Disposition Issues ... 15.5
Authentication Credentials and Idle Clients ... 15.6
Proxies and Caching ... 15.7
Denial of Service Attacks on Proxies ... 15.7.1
Acknowledgments ... 16
References ... 17
Authors' Addresses ... 18
Appendices ... 19
Internet Media Type message/http and application/http ... 19.1
Internet Media Type multipart/byteranges ... 19.2
Tolerant Applications ... 19.3
Differences Between HTTP Entities and RFC 2045 Entities ... 19.4
MIME-Version ... 19.4.1
Conversion to Canonical Form ... 19.4.2
Conversion of Date Formats ... 19.4.3
Introduction of Content-Encoding ... 19.4.4
No Content-Transfer-Encoding ... 19.4.5
Introduction of Transfer-Encoding ... 19.4.6
MHTML and Line Length Limitations ... 19.4.7
Additional Features ... 19.5
Content-Disposition ... 19.5.1
Compatibility with Previous Versions ... 19.6
Changes from HTTP/1 ... 19.6.1
Compatibility with HTTP/1 ... 19.6.2
Changes from RFC 2068 ... 19.6.3
Index ... 20
Full Copyright Statement ... 21
derived from HTTP/1.1, Internet RFC 2616, Fielding, et al.
using rfc2html Revision: 1.8 Date: 2004/09/01 13:21:38 by Dan Connolly
