# HTTP

The Hypertext Transfer protocol is the protocol that powers all of the modern web. It sits at top of the [OSI model](osi.md) of networking/communications, in the application layer.

HTTP is based on the the request-response cycle, where clients send requests to servers which then send responses back to the clients. In this model the clients are usually end users using browsers, but HTTP can be used in a greater variety of contexts.

# Lifecycle of a simple HTTP response

The simplest version of HTTP involves a single request-response cycle on a single connection.

## Assembling all the data

The browser or client determines all the information necessary to the request based on the URL and possibly other information: the protocol, host, port, path to resource, query string and body, and headers.

## Resolve IP address

This involves a [DNS lookup](1), which relies on a large network of DNS servers or nameservers that determine what IP address a hostname (like `example.com`) corresponds to. This network is hierarchical and decentralized and caches the lookups at multiple levels.

## Establishing a TCP connection

Once the browser has received a response to the DNS lookup, it has an IP address and begin to connect with the server. This is achieved using a _three-way handshake_, where the client sends an open request to the server, the server responds, and the client acknowledges the server's response.

## Sending the HTTP request

Now the client can send the HTTP request to the server. The request a request line which indicates the HTTP method and the resource being requested, as well as HTTP headers and an optional body. This request is sent over the TCP connection which ensures that packets are sequenced in the correct order when they arrive.

## Responding to the HTTP request

The server receives and processes the request. It sends an HTTP response back to the client with a status line, headers fields, and a body.

## Closing the connection

As the data from the server arrives, the client sends acknowledgments back to the server indicated that packets were received. When all packets are received, the client initiates a four-way handshake that closes the TCP connection.
