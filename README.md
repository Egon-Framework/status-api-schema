# Status API Schema

[![](https://app.codacy.com/project/badge/Grade/14c1aa3bed5a43a1b92e02679db13337)](https://app.codacy.com/gh/Egon-Framework/status-api-schema/dashboard)
[![](https://github.com/Egon-Framework/status-api-schema/actions/workflows/OpenAPI.yml/badge.svg)](https://github.com/Egon-Framework/status-api-schema/actions/workflows/OpenAPI.yml)

The status API is responsible for tracking Egon runtime metrics within a distributed runtime environment. 
This repository defines the API specification and provides documentation for running associated development tasks.

The API is defined using the [OpenAPI](https://www.openapis.org/) specification (formerly called _swagger_).
Suitable examples are included in the specification for running a small development server. 
All specifications included in this repository are treated as _working documents_ and are updated as necessary to support development on the Egon Framework.

## Developer Guidelines

This project relies on the open source API development stack built by [stoplight](https://stoplight.io/).
The necessary developer tools can be installed with `npm`:

```bash
npm install -g @stoplight/prism-cli @stoplight/spectral
```

### Linting Standards

Project specific API standards are enforced using the [spectral](https://docs.stoplight.io/docs/spectral/) linting utility.
The following command will validate API definitions against requirements defined in the `.spectral.yml` config file:

```bash
spectral lint api/*.yml --fail-severity warn
```

### Running a Mock Server

A mock API instance can be run using [prism](https://docs.stoplight.io/docs/prism/):

```bash
prism mock api/v0.yml -p 4010
```

The mock server will automatically render responses using example data contained within the API specification.
The included examples are limited, but suitable for general development tasks.

### Contract Testing an Existing Server

The `prism` utility can be run in `proxy` mode to validate responses from a running API server.

```bash
prism proxy api/v0.1.yml http://localhost:3000 --errors
```
