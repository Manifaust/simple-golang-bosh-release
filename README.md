This repo provides everything necessary to create a simple BOSH release which will deploy a basic server written in Go. For more details, check out the the [documentation on bosh.io](https://bosh.io/docs/create-release.html).

A lot of the structure is based off of Maria Shaldibina’s great [step-by-step guide](http://mariash.github.io/learn-bosh) on how to create a BOSH release that deploys a Ruby server.

The Golang code in this repo is from the golang.org tutorial on [Writing Web Applications](https://golang.org/doc/articles/wiki/).

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
