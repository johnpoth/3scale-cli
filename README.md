# 3scale CLI

## Overview
This repository contains the command line utility for the API management solution [3scale.net](http://3scale.net).

Its main capabilities include importing an API definition (Open API / Swagger or RAML) into 3scale and:

1) [Importing and API definition (Open API / Swagger or RAML) to define your API](/docs/import-api-definition.md)
2) [Creating interactive documentation (ActiveDocs)](/docs/create-activedocs.md)

Additionally, you can also:

* Create, list, show, update, and delete [services](/docs/services.md)
* Create, list, show, and delete [application plans](/docs/application-plans.md)
* Create, list, show, update, and delete [mapping rules](/docs/mapping-rules.md)
* Create, list, show, update, and delete [methods](/docs/methods.md)
* Create, list, show, update, and delete [metrics](/docs/metrics.md)
* List and show [accounts](/docs/accounts.md)
* Create, list, show, update, delete, suspend, and resume [applications](/docs/applications.md)
* Show, and update [proxy](/docs/proxy.md)
* List, show, and promote [proxy-configs](/docs/proxy-configs.md)

Note: Get familiar with the [3scale terminology](https://support.3scale.net/docs/terminology) reading through our support documentation.

## Install

To install run the command

`npm install -g node-3scale-cli`

Get started looking at the options by running the 'Help' command:
`3scale-cli --help`

To see specific help for each one of the options, for example "activedocs", run:
```3scale-cli activedocs --help```

## Prerequisites

* [3scale](http://3scale.net) account - sign up for free at [http://www.3scale.net](http://www.3scale.net)

## Config

Before using the CLI tool you need to configure it and link it to your 3scale account:

```
3scale-cli config
[ 3scale-cli ] Please answer the following questions to configure 3scale cli.
? 3scale access token 1234567890abc
? 3scale id awesome-api
? 3scale wildcard domain (3scale.net)
[3scale-cli] 3scale cli tool configured
```

![output from terminal](https://www.evernote.com/l/ACV6L21JMwxFm771F9iPNwu3j7eyqLrArkoB/image.png)

Your **3scale id** corresponds to the domain of your [3scale](http://3scale.net) admin portal as in `3scale_id-admin.3scale.net`.  

Your **access token** can be created and obtained according to the [tutorial](https://support.3scale.net/docs/accounts/tokens).

![Access Token](docs/access-token.png)

### Config for on-prem

Some on-prem users had issues regarding hitting 3scale API on onprem installations as reported [here](https://github.com/3scale/3scale-cli/issues/49).
The tool should be called with the `NODE_TLS_REJECT_UNAUTHORIZED` flag.
example: `NODE_TLS_REJECT_UNAUTHORIZED=0 3scale-cli services list`

## Debug/verbose mode
A debug mode is available. To turn it on just add `DEBUG=*` before your calls. It will print all debugs instructions.

Ex: `DEBUG=* 3scale-cli services list`

You can also turn debugs only for a specific part of the tool.
Ex:
`DEBUG=3scale-cli:acounts:* ...`
`DEBUG=3scale-cli:services:* ...`

## Contribute

3scale-cli is open source, and we welcome anybody who wants to participate and contribute!

If you want to fix a bug or make any changes, please [log an issue in GitHub](https://github.com/3scale/3scale-cli/issues) describing the bug
or new feature.

### Get the code

The easiest way to get started with the code is to [create your own fork](http://help.github.com/forking/)
of this repository, and then clone your fork:
```bash
  $ git clone git@github.com:<you>/3scale-cli.git
  $ cd 3scale-cli
  $ git remote add upstream git://github.com/3scale/3scale-cli.git
```
At any time, you can pull changes from the upstream and merge them onto your master:
```bash
  $ git checkout master               # switches to the 'master' branch
  $ git pull upstream master          # fetches all 'upstream' changes and merges 'upstream/master' onto your 'master' branch
  $ git push origin                   # pushes all the updates to your fork, which should be in-sync with 'upstream'
```
The general idea is to keep your 'master' branch in-sync with the 'upstream/master'.

### Make a fix

If you want to fix a bug or make any changes, please [log an issue in GitHub](https://github.com/3scale/3scale-cli/issues) describing the bug
or new feature. Then we highly recommend making the changes on a branch named with the issue number. For example, this command creates
a branch for the issue #17 :
```bash
  $ git checkout -b 3scale-cli-issue-17
```
After you're happy with your changes and a full build (with unit tests) runs successfully, commit your
changes on your topic branch. Then it's time to check for and pull any recent changes that were made in
the official repository:
```bash
  $ git checkout master               # switches to the 'master' branch
  $ git pull upstream master          # fetches all 'upstream' changes and merges 'upstream/master' onto your 'master' branch
  $ git checkout 3scale-cli-issue-17   # switches to your topic branch
  $ git rebase master                 # reapplies your changes on top of the latest in master
                                      # (i.e., the latest from master will be the new base for your changes)
```

Push your changes and [generate a pull-request](http://help.github.com/pull-requests/)

Please try to create one commit per feature or fix, generally the easiest way to do this is via [git squash](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History#Squashing-Commits).
This makes reverting changes easier, and avoids needlessly polluting the repository history with checkpoint commits.

### Building 3scale-cli

#### Requirements
- NodeJS

#### Building
```bash
  $ npm install
```

#### Running
```bash
  $ bin/3scale-api
```

## License

The MIT License (MIT)

Copyright (c) 2015 3scale Inc.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
