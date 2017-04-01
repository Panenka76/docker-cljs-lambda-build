# cljs-lambda docker image

This is a docker image for building a ClojureScript project that installs AWS Lambda functions. Its main function is to be used on CircleCI 2.0 as a build container.

## What's in it?
1. This image is based upon the official [Node.js image](https://hub.docker.com/_/node/)
2. [Leiningen](https://leiningen.org/) and OpenJDK 7
3. [Serverless](https://github.com/serverless/serverless) and the [cljs-lambda](https://github.com/nervous-systems/cljs-lambda) plugin for it

## Usage
You can use any of the build tools provided by the projects in the list above, but probably you'd like to use a circle.yml file that looks something like this

```yml

```