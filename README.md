# LeaseQ REST API Documentation

Following document outlines the LeaseQ API usage along with authentication.  This document is being constantly updated as we develop new APIs and processes.

## Environments

### Production
https://dashq.leaseq.com/api

### Dev/Test
http://dashq-demo.herokuapp.com/api

## APIs

### Authentication

Endpoints for authentication.

* [Login](login/post.md) : `POST /login`

### Applications

Endpoints for managing LeaseQ credit applications.

* [Create an Application](applications/post.md) : `POST /applications`
* [Update an Application](applications/put.md) : `PUT /applications`
* [Retrieve an Application](applications/get.md) : `GET /applications/{application_id}`
* [Update an Application](applications/patch.md) : `PATCH /applications/{application_id}`
