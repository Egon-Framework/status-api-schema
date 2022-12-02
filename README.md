# Egon Status API
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/14c1aa3bed5a43a1b92e02679db13337)](https://www.codacy.com/gh/Egon-Framework/status-api/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Egon-Framework/status-api&amp;utm_campaign=Badge_Grade)
[![Documentation](https://github.com/Egon-Framework/status-api/actions/workflows/Documentation.yml/badge.svg)](https://github.com/Egon-Framework/status-api/actions/workflows/Documentation.yml)
[![OpenAPI Standard](https://github.com/Egon-Framework/status-api/actions/workflows/OpenAPI.yml/badge.svg)](https://github.com/Egon-Framework/status-api/actions/workflows/OpenAPI.yml)

The status API is responsible for exposing Egon system and pipeline metrics.
This repository defines the API specification and provides documentation for spinning up a local development instance.

The API is defined using the [OpenAPI](https://www.openapis.org/) specification (formally called _swagger_).
Suitable examples are included in the specification for running a small development server.

## Working on a Local Development

The following sections provide instructions for setting up a simple development environment.

### API Editing

Many IDEs include utilities for linting the OPENAPI specification.
If you're looking for a dedicated editing tool, swagger provides
an [open source editor](https://swagger.io/tools/swagger-editor/).
You can download and run the dockerized editor using the commands below:

```bash
docker pull swaggerapi/swagger-editor
docker run -d -p 8080:8080 swaggerapi/swagger-editor
```

### Running a Mock Server

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
For the mock server instance, any token value will work.

```bash
curl  http://127.0.0.1:4010/pipeline/123?token=1234
```

### Previewing the Documentation

A local documentation preview can be generated using the [elements](https://stoplight.io/open-source/elements) utility.
Install the utility with `npm`:

```bash
npm install -g @skriptfabrik/elements-cli
```

Use the `preview` command to launch a live preview.
By specifying the `-w` argument, elements will watch for file changes and automatically reload the documentation.

```bash
elements preview -w api.yml
```

By default, the documentation will be accessible on [http://localhost:8000/](http://localhost:8000/).
