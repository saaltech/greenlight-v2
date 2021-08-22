# Greenlight

![Coverage
!Status](https://coveralls.io/repos/github/bigbluebutton/greenlight/badge.svg?branch=master)
![Docker Pulls](https://img.shields.io/docker/pulls/bigbluebutton/greenlight.svg)

Greenlight is a simple front-end interface for your BigBlueButton server. At its heart, Greenlight provides a minimalistic web-based application that allows users to:

  * Signup/Login with Google, Office365, OpenID Connect, or through the application itself.
  * Manage your account settings and user preferences.
  * Create and manage your own personal rooms ([BigBlueButton](https://github.com/bigbluebutton/bigbluebutton) sessions).
  * Invite others to your room using a simple URL.
  * View recordings and share them with others.

Interested? Try Greenlight out on our [demo server](https://demo.bigbluebutton.org/gl)!

Greenlight is also completely configurable. This means you can turn on/off features to make Greenlight fit your specific use case. For more information on Greenlight and its features, see our [documentation](http://docs.bigbluebutton.org/greenlight/gl-install.html).

For a overview of how Greenlight works, checkout our Introduction to Greenlight Video:

[![GreenLight Overview](https://img.youtube.com/vi/Hso8yLzkqj8/0.jpg)](https://youtu.be/Hso8yLzkqj8)

## Installation on a BigBlueButton Server

Greenlight is designed to work on a [BigBlueButton 2.0](https://github.com/bigbluebutton/bigbluebutton) (or later) server.

For information on installing Greenlight, checkout our [Installing Greenlight on a BigBlueButton Server](http://docs.bigbluebutton.org/greenlight/gl-install.html#installing-on-a-bigbluebutton-server) documentation.

## Source Code & Contributing

Greenlight is built using Ruby on Rails. Many developers already know Rails well, and we wanted to create both a full front-end to BigBlueButton but also a reference implementation of how to fully leverage the [BigBlueButton API](http://docs.bigbluebutton.org/dev/api.html).

We invite you to build upon Greenlight and help make it better. See [Contributing to BigBlueButton](http://docs.bigbluebutton.org/support/faq.html#contributing-to-bigbluebutton).

We invite your feedback, questions, and suggests about Greenlight too. Please post them to the [Greenlight mailing list](https://groups.google.com/forum/#!forum/bigbluebutton-greenlight).

To help with organization and consistency, we have implemented a Pull Request template that must be used for all Pull Requests. This template helps ensure that the project maintainers can review all PRs in a timely manner. When creating a Pull Request, please provide as much information as possible.

## Steps to run this application (development)

First you need to modify `.env` file, you need to add modify 2 variables

`SAFE_HOSTS=127.0.0.1`<br />
`SECRET_KEY_BASE=40117a0a7347b724ac7ac91a77aeabd9ae9aa6201b2654fc71174c1574382995ee27d1037dbee4de2830e974faf5e537929118a2872cd865d498a1a00cdf0334` (for which you need to install the bbb server and generate or get credentials from devops team)<br />
`BIGBLUEBUTTON_ENDPOINT=https://bbb-v2.saal.ai/bigbluebutton/` (your bbb server endpoint)<br />
`BIGBLUEBUTTON_SECRET=c2NGmHhAlLFzKIDckjnFNLEbIe6Jjm05zffACsVywww` (your bbb secret)<br />
`ENABLE_SSL=false`<br />

Then run the following command

`./scripts/image_build.sh bbb-saal release-v2 && docker-compose up`

Here `bbb-saal` in the above command refers to image name and `release-v2` refers to the image version

This command will build the  image with tag `scr.saal.ai/bbb-saal:release-v2` and push it to `scr.saal.ai` repository, and start the docker.

You have to configure your nginx server to point to this, so use `greenlight.nginx` file and open http://127.0.0.1

And now you can start customizing the application by just start editing the html and css files in `app/views`


## Steps to run this application (production)

In production, to already configured bbb server,  use the same above steps instead set 

`ENABLE_SSL=true` in `.env` <br/>

Also run 

`./scripts/image_build.sh bbb-saal release-v2`

And replace the greenlight image name with 

`scr.saal.ai/bbb-saal:release-v2`

## Author 

shaik@saal.ai 