# LeaseQ REST API Documentation

Following document outlines the LeaseQ API usage along with authentication.  This document is being constantly updated as we develop new APIs and processes.

## Environments

### Production
ht&#8203;tps://dashq.leaseq.com/api

### Dev/Test
ht&#8203;tp://dashq-demo.leaseq.com/api

## APIs

### Authentication

Endpoints for authentication.

* [Login](login/post.md) : `POST /login`

### Applications

Endpoints for managing LeaseQ credit applications.

* [Create an Application](applications/post.md) : `POST /applications`
* [Update an existing Application](applications/put.md) : `PUT /applications/{application_id}`
* [Retrieve an Application](applications/get.md) : `GET /applications/{application_id}`
* [Update the status of an Application](applications/patch.md) : `PATCH /applications/{application_id}`
