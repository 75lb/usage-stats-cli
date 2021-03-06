[![view on npm](http://img.shields.io/npm/v/usage-stats-cli.svg)](https://www.npmjs.org/package/usage-stats-cli)
[![npm module downloads](http://img.shields.io/npm/dt/usage-stats-cli.svg)](https://www.npmjs.org/package/usage-stats-cli)
[![Build Status](https://travis-ci.org/75lb/usage-stats-cli.svg?branch=master)](https://travis-ci.org/75lb/usage-stats-cli)
[![Coverage Status](https://coveralls.io/repos/github/75lb/usage-stats-cli/badge.svg?branch=master)](https://coveralls.io/github/75lb/usage-stats-cli?branch=master)
[![Dependency Status](https://david-dm.org/75lb/usage-stats-cli.svg)](https://david-dm.org/75lb/usage-stats-cli)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](https://github.com/feross/standard)

# usage-stats-cli

A minimal, offline-friendly [Google Analytics Measurement Protocol](https://developers.google.com/analytics/devguides/collection/protocol/v1/) client for tracking usage statistics in shell and javascript applications.

This is a low-level API client, it doesn't hold any opinion of how usage tracking should be done. If you're looking for a convention which leverages the power and flexibility of [Custom Metrics and Dimensions](https://support.google.com/analytics/answer/2709828?hl=en&ref_topic=2709827), take a look at [app-usage-stats](https://github.com/75lb/app-usage-stats).

## Synopsis

Tracking statistics in shell scripts:

```sh
# Track an event: category 'Backup', action 'start'
usage-stats event --tid UA-98765432-1 --ec Backup --ea start

# Perform the backup
cp files/** backup/

# Track an event: category 'Backup', action 'complete'
usage-stats event --tid UA-98765432-1 --ec Backup --ea complete
```

## Protocol Parameters

See [here](https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters) for the full list of Google Analytics Measurement Protocol parameters.

### Sent by default

All parameters are send on demand, beside this list.

* Operating System version (sent in the UserAgent)
* [Client ID](https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters#cid) (a random UUID, generated once per OS user and stored)
* [Language](https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters#ul) (`process.env.LANG`, if set)
* [Screen resolution](https://developers.google.com/analytics/devguides/collection/protocol/v1/parameters#sr) (terminal rows by columns, by default)

## CLI Reference

To install the command line client:

```
$ npm install -g usage-stats-cli
```

Running the tool with no arguments will print the usage guide:

<pre><code><strong>usage-stats</strong>

  A minimal, offline-friendly Google Analytics Measurement Protocol client for
  tracking usage statistics in shell and javascript applications.

<strong>Synopsis</strong>

  $ usage-stats &lt;command&gt; &lt;command-options&gt;
  $ usage-stats &lt;command&gt; --help

<strong>Commands</strong>

  screenview   Track a screenview
  event        Track an event
  exception    Track an exception
</code></pre>

* * *

&copy; 2016-17 Lloyd Brookes \<75pound@gmail.com\>. Documented by [jsdoc-to-markdown](https://github.com/jsdoc2md/jsdoc-to-markdown).
