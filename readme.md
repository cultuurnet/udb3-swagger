# WARNING!

This repository is obsolete. See https://docs.publiq.be for the latest UiTdatabank API documentation.

# UDB3 Swagger

[![Build Status](https://travis-ci.org/cultuurnet/udb3-swagger.svg?branch=master)](https://travis-ci.org/cultuurnet/udb3-swagger)

Swagger documentation for the udb3 jsonld api.

## Guidelines

The following guidelines should always be followed when making changes, even though existing docs may not always follow them.

**The examples in these guidelines do not necessarily reflect real endpoints.**

### Resource collections

Resource collections should always be plural, and end in a trailing slash because they represent a directory of resources.

Examples:
- Get all users: `GET /users/`
- Add a new user: `POST /users/`

### Filtering resource collections

Resource collections are always filtered using query parameters.

Examples:
- Get all users with a specific role: `GET /users/?role=...`

### Resource detail

Resources are subdirectories of their collection, identified by an id or slug.
They have no trailing slash.

Examples:
- Get a specific user: `GET /users/{userId}`
- Create a user with a specific id: `PUT /users/{userId}`
- Update a specific user: `PATCH /users/{userId}`
- Delete a specific user: `DELETE /users/{userId}`

### Singletons

Singletons are resources of which only one can ever exist. Singletons are thus always singular.
They have no trailing slash, as they represent a single resource.

Examples:
- Update the title of an event: `PUT /events/{eventId}/title`

### PATCH requests

PATCH requests should differentiate their different payload types by adding a `domain-model` value to the `content-type` header of the request.

Example:

    PATCH /events/{eventId}
    Content-Type: application/ld+json;domain-model=SetTitle
    
    {
        "title": "New title"
    }
    
For more information, see: [5 levels of media type (5LMT)](http://byterot.blogspot.be/2012/12/5-levels-of-media-type-rest-csds.html)

### Casing

All endpoints should be lowercase, and use dashes for separating multiple words in a single slug.
Wildcards are camelcased, starting with a lowercase letter.

Examples:
- `PUT /events/{eventId}/typical-age-range`

## Contributing

Install the npm dependencies:

    npm install
    
Validate your changes:

    npm run validate-swagger-lint
    npm run validate-swagger-schema
    
 The same validation is run on Travis for every push event.
