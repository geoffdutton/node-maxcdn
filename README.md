# node-stackpath

StackPath API for Node.js: [https://api.stackpath.com/](https://api.stackpath.com/)

[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com)
[![Build Status](https://travis-ci.org/geoffdutton/node-stackpath.svg?branch=master)](https://travis-ci.org/geoffdutton/node-stackpath) [![Greenkeeper badge](https://badges.greenkeeper.io/geoffdutton/node-stackpath.svg)](https://greenkeeper.io/)

> Note: Unit tests have been run against latest 4.x and 6.x versions of Node.js.

## Install

```
$ npm install stackpath
```

## Usage

#### Initialize

```
const stackpath = require('stackpath').create('COMPANY_ALIAS', 'CONSUMER_KEY', 'CONSUMER_SECRET');
```

#### `stackpath.get`

```
stackpath.get('reports/stats/daily', function(err, results) {
    if (err) {
        console.trace(err);
        return;
    }
    console.dir(results);
});
```

#### `stackpath.put`

```
var updates = {
    street1: '555 Some St.',
    street2: 'Suite #1'
};
maxcdn.put('account/address', updates, function(err, results) {
    if (err) {
        console.trace(err);
        return;
    }
    console.dir(results);
});
```

#### `stackpath.post`

```
stackpath.post('sites', { name: 'testname', url: 'http://www.example.com' }, function(err, results) {
    if (err) {
        console.trace(err);
        return;
    }
    console.dir(results);
});
```

#### `stackpath.del`

> Has alias of `stackpath.delete`.

```
const zoneId = '121212';

// full cache
stackpath.del(`sites/${zoneId}/cache`, function(err, results) {
    if (err) {
        console.trace(err);
        return;
    }
    if (results.code === 200) {
        console.log('SUCCESS!');
    }
});

// specific files
const files = { files: [ '/master.css', '/another.css' ] };
stackpath.del(`sites/${zoneId}/cache`, files, function(err, results) {
    if (err) {
        console.trace(err);
        return;
    }
    if (results[0].code === 200) {
        console.log('SUCCESS: %s', files.files[0]);
    }
    if (results[1].code === 200) {
        console.log('SUCCESS: %s', files.files[1]);
    }
});
```

## Running Tests

#### Unit Tests

```
$ npm test
```

#### Integration Tests

```
$ STACKPATH_ALIAS=alias STACKPATH_KEY=key STACKPATH_SECRET=secret npm run int
```

> **Troubleshooting:**
>
> Ensure that you `STACKPATH_ALIAS`, `STACKPATH_KEY` and `STACKPATH_SECRET` values are correct and that you're running integration on a host with a whitelisted IP address.

