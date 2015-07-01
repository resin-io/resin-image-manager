resin-image-manager
-------------------

[![npm version](https://badge.fury.io/js/resin-image-manager.svg)](http://badge.fury.io/js/resin-image-manager)
[![dependencies](https://david-dm.org/resin-io/resin-image-manager.png)](https://david-dm.org/resin-io/resin-image-manager.png)
[![Build Status](https://travis-ci.org/resin-io/resin-image-manager.svg?branch=master)](https://travis-ci.org/resin-io/resin-image-manager)
[![Build status](https://ci.appveyor.com/api/projects/status/2nxg1uydksvey0g8?svg=true)](https://ci.appveyor.com/project/jviotti/resin-image-manager)

Manage device base operating systems resources with caching support.

Role
----

The intention of this module is to provide low level access to how a Resin.io device image is downloaded, cached and evaluated for freshness.

**THIS MODULE IS LOW LEVEL AND IS NOT MEANT TO BE USED BY END USERS DIRECTLY**.

Installation
------------

Install `resin-image-manager` by running:

```sh
$ npm install --save resin-image-manager
```

Documentation
-------------


* [manager](#module_manager)
  * [.get(slug)](#module_manager.get) ⇒ <code>ReadStream</code>
  * [.cleanCache()](#module_manager.cleanCache) ⇒ <code>Promise</code>

<a name="module_manager.get"></a>
### manager.get(slug) ⇒ <code>ReadStream</code>
This function saves a copy of the downloaded image in the cache directory setting specified in [resin-settings-client](https://github.com/resin-io/resin-settings-client).

**Kind**: static method of <code>[manager](#module_manager)</code>  
**Summary**: Get a device operating system image  
**Returns**: <code>ReadStream</code> - image readable stream  
**Access:** public  

| Param | Type | Description |
| --- | --- | --- |
| slug | <code>String</code> | device type slug |

**Example**  
```js
manager.get('raspberry-pi').then (stream) ->
	stream.pipe(fs.createWriteStream('foo/bar.img'))
```
<a name="module_manager.cleanCache"></a>
### manager.cleanCache() ⇒ <code>Promise</code>
Useful to manually force an image to be re-downloaded.

**Kind**: static method of <code>[manager](#module_manager)</code>  
**Summary**: Clean the saved images cache  
**Access:** public  
**Example**  
```js
manager.cleanCache()
```

Support
-------

If you're having any problem, please [raise an issue](https://github.com/resin-io/resin-image-manager/issues/new) on GitHub and the Resin.io team will be happy to help.

Tests
-----

Run the test suite by doing:

```sh
$ gulp test
```

Contribute
----------

- Issue Tracker: [github.com/resin-io/resin-image-manager/issues](https://github.com/resin-io/resin-image-manager/issues)
- Source Code: [github.com/resin-io/resin-image-manager](https://github.com/resin-io/resin-image-manager)

Before submitting a PR, please make sure that you include tests, and that [coffeelint](http://www.coffeelint.org/) runs without any warning:

```sh
$ gulp lint
```

License
-------

The project is licensed under the MIT license.
