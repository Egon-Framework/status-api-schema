# Egon Status API
[![Codacy Badge](https://app.codacy.com/project/badge/Grade/14c1aa3bed5a43a1b92e02679db13337)](https://www.codacy.com/gh/Egon-Framework/status-api/dashboard?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=Egon-Framework/status-api&amp;utm_campaign=Badge_Grade)
[![Documentation](https://github.com/Egon-Framework/status-api/actions/workflows/Documentation.yml/badge.svg)](https://github.com/Egon-Framework/status-api/actions/workflows/Documentation.yml)
[![OpenAPI Standard](https://github.com/Egon-Framework/status-api/actions/workflows/OpenAPI.yml/badge.svg)](https://github.com/Egon-Framework/status-api/actions/workflows/OpenAPI.yml)

The status API is responsible for exposing Egon runtime metrics for use by the Egon visualization dashboard.
This repository defines the API specification and provides documentation for running associated development tasks.

The API is defined using the [OpenAPI](https://www.openapis.org/) specification (formally called _swagger_).
Suitable examples are included in the specification for running a small development server.

## Development Guidelines

This project relies on the open source API development stack built by [stoplight](https://stoplight.io/).
The necessary developer tools can be installed with `npm`:

```bash
npm install -g @stoplight/prism-cli @stoplight/spectral
```

### Linting Standards

Project specific API standards are enforce using the `spectral` linting utility.
The following command will validate API definitions against requirements defined in the `.spectral.yml` config file:

```bash
spectral lint api/*.yml --fail-severity warn
```

### Running a Dev Server

A mock API instance can be spun up using [prism](https://docs.stoplight.io/docs/prism/674b27b261c3c-overview):

```bash
prism mock api/v0.yml -p 4010
```

The mock server will automatically render responses using example data contained within the API specification.
The included examples are limited, but suitable for most development tasks.

When performing queries against the mock session, don't forget to provide a dummy auth token.
While running a mock server, any token value will work. For example:

```bash
curl  http://127.0.0.1:4010/pipeline/123?token=1234
```
