# HTTP Status Codes Cheat Sheet

Here's a quick reference for common HTTP status codes and their meanings:

## 1xx Informational

- **100 Continue:** The server acknowledges the client's request and is waiting for the client to send the rest of the request.

- **101 Switching Protocols:** The server agrees to switch protocols as requested by the client.

## 2xx Success

- **200 OK:** The request was successful, and the server has returned the requested data.

- **201 Created:** The request was successful, and a new resource was created as a result.

- **204 No Content:** The request was successful, but there is no additional content to send in the response.

## 3xx Redirection

- **300 Multiple Choices:** The requested resource has multiple possible responses. The client should choose one.

- **301 Moved Permanently:** The requested resource has been permanently moved to a new location.

- **304 Not Modified:** The client's cached version of the requested resource is still valid, so the server responds with no content.

## 4xx Client Errors

- **400 Bad Request:** The server cannot understand the client's request, usually due to malformed syntax.

- **401 Unauthorized:** The client needs to authenticate to get the requested response.

- **403 Forbidden:** The client does not have permission to access the requested resource.

- **404 Not Found:** The requested resource could not be found on the server.

- **429 Too Many Requests:** The client has sent too many requests to the server in a given amount of time.

## 5xx Server Errors

- **500 Internal Server Error:** The server encountered an error while processing the request.

- **501 Not Implemented:** The server does not support the functionality required to fulfill the request.

- **502 Bad Gateway:** The server, while working as a gateway to get a response needed to handle the request, got an invalid response.

- **503 Service Unavailable:** The server is not ready to handle the request, usually due to maintenance or overloading.

- **504 Gateway Timeout:** The server, while acting as a gateway or proxy, did not receive a timely response from an upstream server.

---

This cheat sheet is a quick reference for common HTTP status codes. For more details, refer to the [HTTP Status Code Definitions](https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml) document.

---
**Note:** This cheat sheet is a reference guide and might not cover all scenarios. Always refer to the official documentation and consult with experienced developers for complex projects.

Feel free to create a pull request and customize and format this cheat sheet according to your preferences.
