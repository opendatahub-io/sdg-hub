# SDG Podman Testing

This repository contains Docker configuration for testing SDG Hub components.

## Prerequisites

- Podman installed on your system
- Valid OpenAI API key

## Building the Image

To build the image for testing (currently targeting the integration test PR in upstream), run:

```bash
podman build -f Dockerfile.sdg-test --build-arg GIT_BRANCH=feat/integration-test-base -t sdg-hub-tester:latest .
```

## Running Integration Tests

To run the integration tests, execute:

```bash
podman run --rm -e OPENAI_API_KEY="your-api-key-here" sdg-hub-tester:latest
```

**Note:** Replace `"your-api-key-here"` with your actual OpenAI API key.

## Dockerfile Details

The Dockerfile (`Dockerfile.sdg-test`) is configured to:
- Use the specified Git branch via build argument
- Set up the testing environment
- Run integration tests when the container starts

## Cleanup

The `--rm` flag automatically removes the container after it finishes running, so no manual cleanup is required.
