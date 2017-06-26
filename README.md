This repo provides everything necessary to create a simple BOSH release which will deploy a basic server written in Go. For more details, check out the the [documentation on bosh.io](https://bosh.io/docs/create-release.html).

A lot of the structure of this repo comes from Maria Shaldibina’s great [step-by-step guide](http://mariash.github.io/learn-bosh) on how to create a BOSH release that deploys a Ruby server.

The Golang code in this repo is from the golang.org tutorial on [Writing Web Applications](https://golang.org/doc/articles/wiki/).

## Assumptions

This release is configured to compile to a Linux environment. You'll have to add another Go compiler and some extra logic to support other OS's.

I'm using a stemcell meant for deploying to a BOSH environment set up using VirtualBox or BOSH-Lite. If you're deploying to AWS or GCP, you'll have to specify a different stemcell.

The BOSH team has created a [quick and easy guide to deploying BOSH on VirtualBox](https://github.com/cloudfoundry/bosh-deployment/blob/master/docs/bosh-lite-on-vbox.md). It's what I used during my own testing.

## Quick Start

```
$ git clone https://github.com/Manifaust/simple-golang-bosh-release.git
$ cd simple-golang-bosh-release
$ bosh create-release
$ bosh -e <environment_name> upload-release
$ bosh -e <environment_name> -d simple-go deploy manifest.yml
$ curl 10.244.0.18:8080/crustaceans
Hi there, I love crustaceans!
```

## Customizing the App

The entire server code resides in [`src/simple_server/hello.go`](src/simple_server/hello.go), you can customize it to do more. If you need greater control over the build process, take a look at [`packages/simple_server/packaging`](packages/simple_server/packaging).

After making changes to the release, just commit your code and run `bosh create-release` (and subsequent steps) again.
