# LeaseQ REST API Documentation

This documentation outlines LeaseQ API usage for partners who are building integrations. This document is being constantly updated as LeaseQ develops new APIs and processes.

## Environments

### Production
ht&#8203;tps://dashq.leaseq.com/api

### Dev/Test
ht&#8203;tp://dashq-demo.leaseq.com/api

## Authorization Header
Most LeaseQ APIs require the caller to include an authentication token in the header of the request. You can obtain an authentication token using the [Login](login/post.md) API. Once you have the authentication token, include it via the **Authorization** header in subsequent API requests. The format for the **Authorization** header is as follows.

```
Authorization: LeaseQ $Auth_Token
```

## APIs

* [Login](login/post.md)
* [Applications](applications/README.md)
* [Lenders](lenders/README.md)

### API Limits
The following limits are imposed on clients accessing these APIs.

| Limit | Value |
|:-----|:------|
|Request body size| 25 MB|