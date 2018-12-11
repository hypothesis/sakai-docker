# sakai-docker

Docker container for the stable version of [Sakai v12](https://github.com/sakaiproject/sakai).

This project exists to help with testing of the [Hypothesis
LMS](https://github.com/hypothesis/lms) integration in Sakai.

Installation requires [Docker Compose](https://docs.docker.com/compose/).

## Setup

First, run a Git submodule update to fetch/update the source code for Sakai.

```sh
git submodules update --init
```

To build the Docker image for Sakai and launch containers for Sakai and MySQL,
run:

```sh
docker-compose up
```

The first time this command is run the Docker image for Sakai will be built,
which can take 10 minutes or more. Additionally when the Sakai starts for the
first time it will spend several minutes initializing.

## Logging into Sakai

Once the Sakai container image has been built and the container is created,
you can access Sakai by browsing to http://localhost:8080.

The default admin user is `admin` and the password is `admin`.

## Installing the Hypothesis LTI tool

To test an LTI tool, you will need to:

1. Create a new "project site".
   - Click "Worksite Setup" in the left navbar
   - Select "Build your own site" => "project site"
   - Click "Continue".
2. Enter a title for the site and click "Continue".
3. On the "Project Site Tools" page, check the "External Tool" option and click
   Continue.
4. Click "Continue" on the Project Site Access page
5. Click "Create Site" on the confirmation page.
6. Select the new site in the list of sites. It should be displayed as active
   in the tabs at the top.
7. Click the "External Tool" link in the left navbar and then click "Edit"
   to configure it.
8. Register a new LMS application instance at https://hypothes.is/welcome
   and enter the launch URL, and consumer key and secret in Sakai.

## Troubleshooting

If you have problems building or running the Docker container on macOS, you may
need to increase the memory allowance for Docker Engine up from the default of
2GB to 3GB or more.

This can be done in the "Advanced" section of Docker for Mac's Preferences UI.

## References

[Quick Start from Source](https://github.com/sakaiproject/sakai/wiki/Quick-Start-from-Source)
