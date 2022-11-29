# Egon Status API

The status API is responsible for exposing Egon metrics for use by the Egon visualization dashboard.
This repository defines the API specification and provides documentation for spinning up local development instances.

The API is defined using the [OpenAPI](https://www.openapis.org/) specification (formally called _swagger_).
Suitable examples are included in the specification for running a small development server.

## Working on a Local Machine

This project doesn't require any special configuration or setup.
For convenience, instructions are provided for getting a simple development environment up and running.

### API Editing

Many IDEs include utilities for linting the OPENAPI specification.
If you're looking for a dedicated editing tool, swagger provides
an [open source editor](https://swagger.io/tools/swagger-editor/).
You can download and run the dockerized editor using the commands below:

```bash
docker pull swaggerapi/swagger-editor
docker run -d -p 8080:8080 swaggerapi/swagger-editor
```

### Running a Dev Server

A mock API instance can be spun up using [prism](https://docs.stoplight.io/docs/prism/674b27b261c3c-overview).
Install the utility with `npm`:

```bash
npm install -g @stoplight/prism-cli
```

Then spin up a local instance as follows:

```bash
prism mock api.yml
```

When performing queries against the mock session, don't forget to provide a dummy auth token.
When running a mock server, any token value will work.

```bash
curl  http://127.0.0.1:4010/pipeline/123?token=1234
```
