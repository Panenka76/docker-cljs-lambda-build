# cljs-lambda docker image

This is a docker image for building a ClojureScript project that installs AWS Lambda functions through the [cljs-lambda](https://github.com/nervous-systems/cljs-lambda) plugin for the [Serverless Framework](https://github.com/serverless/serverless). Its main function is to be used on CircleCI 2.0 as a build container.

## What's in it?
1. This image is based upon the official [Clojure](https://hub.docker.com/_/clojure/) image version [lein-2.7.1](https://github.com/Quantisan/docker-clojure/blob/f0fd68d6a197b4d1852aefab698b35ce1ea9881e/debian/lein/Dockerfile)
2. [Node.js](https://nodejs.org/) version 7.8.0
3. [Serverless](https://github.com/serverless/serverless) version 1.10.1

## Usage
You can use any of the build tools provided by the projects in the list above, but probably you'd like to use a circle.yml file that looks something like this

```yaml
version: 2
jobs:
  build:
    docker:
      - image: panenka76/cljs-lambda-build
    working_directory: ~/tmp
    steps:
      - checkout
      - run:
          name: Install CLJS Lambda plugin
          command: npm install --save serverless-cljs-plugin
      - deploy:
          command: |
            if [ "${CIRCLE_BRANCH}" == "develop" ]; then
              serverless deploy --stage dev
            fi

```