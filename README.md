# api documentation for  [rpi-gpio (v0.7.0)](https://github.com/JamesBarwell/rpi-gpio.js#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-rpi-gpio.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-rpi-gpio) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-rpi-gpio.svg)](https://travis-ci.org/npmdoc/node-npmdoc-rpi-gpio)
#### Control Raspberry Pi GPIO pins with node.js

[![NPM](https://nodei.co/npm/rpi-gpio.png?downloads=true)](https://www.npmjs.com/package/rpi-gpio)

[![apidoc](https://npmdoc.github.io/node-npmdoc-rpi-gpio/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-rpi-gpio_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-rpi-gpio/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-rpi-gpio/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-rpi-gpio/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "James Barwell",
        "email": "jb@jamesbarwell.co.uk"
    },
    "bugs": {
        "url": "https://github.com/JamesBarwell/rpi-gpio.js/issues"
    },
    "dependencies": {
        "async": "1.x",
        "debug": "2.x",
        "epoll": "0.1.x"
    },
    "description": "Control Raspberry Pi GPIO pins with node.js",
    "devDependencies": {
        "istanbul": "~0.2.7",
        "mocha": "~1.18.2",
        "sinon": "~1.9.0"
    },
    "directories": {
        "test": "test",
        "integration": "integration"
    },
    "dist": {
        "shasum": "a71ea43a2701d13ae9003ef0e46c6bcd3dc413ca",
        "tarball": "https://registry.npmjs.org/rpi-gpio/-/rpi-gpio-0.7.0.tgz"
    },
    "gitHead": "a864592b032310b7f3c369e3de0b6864feef3a19",
    "homepage": "https://github.com/JamesBarwell/rpi-gpio.js#readme",
    "keywords:": [
        "raspberry",
        "pi",
        "gpio"
    ],
    "license": "MIT",
    "main": "rpi-gpio.js",
    "maintainers": [
        {
            "name": "jamesbarwell",
            "email": "jb@jamesbarwell.co.uk"
        }
    ],
    "name": "rpi-gpio",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/JamesBarwell/rpi-gpio.js.git"
    },
    "scripts": {
        "coverage": "istanbul cover _mocha",
        "int": "mocha test/integration",
        "spec": "mocha --reporter spec",
        "test": "mocha"
    },
    "version": "0.7.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module rpi-gpio](#apidoc.module.rpi-gpio)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>destroy (cb)](#apidoc.element.rpi-gpio.destroy)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>input (channel, cb)](#apidoc.element.rpi-gpio.input)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>output (channel, value, cb)](#apidoc.element.rpi-gpio.output)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>read (channel, cb)](#apidoc.element.rpi-gpio.read)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>reset ()](#apidoc.element.rpi-gpio.reset)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>setMode (mode)](#apidoc.element.rpi-gpio.setMode)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>setup (channel, direction, edge, onSetup)](#apidoc.element.rpi-gpio.setup)
1.  [function <span class="apidocSignatureSpan">rpi-gpio.</span>write (channel, value, cb)](#apidoc.element.rpi-gpio.write)
1.  number <span class="apidocSignatureSpan">rpi-gpio.</span>_eventsCount
1.  object <span class="apidocSignatureSpan">rpi-gpio.</span>_events
1.  object <span class="apidocSignatureSpan">rpi-gpio.</span>domain
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>DIR_IN
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>DIR_OUT
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>EDGE_BOTH
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>EDGE_FALLING
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>EDGE_NONE
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>EDGE_RISING
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>MODE_BCM
1.  string <span class="apidocSignatureSpan">rpi-gpio.</span>MODE_RPI



# <a name="apidoc.module.rpi-gpio"></a>[module rpi-gpio](#apidoc.module.rpi-gpio)

#### <a name="apidoc.element.rpi-gpio.destroy"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>destroy (cb)](#apidoc.element.rpi-gpio.destroy)
- description and source-code
```javascript
destroy = function (cb) {
    var tasks = Object.keys(exportedOutputPins)
        .concat(Object.keys(exportedInputPins))
        .map(function(pin) {
            return function(done) {
                removeListener(pin, pollers)
                unexportPin(pin, done);
            }
        });

    async.parallel(tasks, cb);
}
```
- example usage
```shell
...
gpio.setup(16, gpio.DIR_OUT, pause);

function pause() {
    setTimeout(closePins, 2000);
}

function closePins() {
    gpio.destroy(function() {
        console.log('All pins unexported');
    });
}
'''


### Voltage cycling a pin
...
```

#### <a name="apidoc.element.rpi-gpio.input"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>input (channel, cb)](#apidoc.element.rpi-gpio.input)
- description and source-code
```javascript
input = function (channel, cb) {
    if (typeof cb !== 'function') {
        throw new Error('A callback must be provided')
    }

    var pin = getPinForCurrentMode(channel);

    if (!exportedInputPins[pin] && !exportedOutputPins[pin]) {
        return process.nextTick(function() {
            cb(new Error('Pin has not been exported'));
        });
    }

    fs.readFile(PATH + '/gpio' + pin + '/value', 'utf-8', function(err, data) {
        if (err) {
            return cb(err)
        }
        data = (data + '').trim() || '0';
        debug('read pin %s with value %s', pin, data);
        return cb(null, data === '1');
    });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.rpi-gpio.output"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>output (channel, value, cb)](#apidoc.element.rpi-gpio.output)
- description and source-code
```javascript
output = function (channel, value, cb) {
    var pin = getPinForCurrentMode(channel);
    cb = cb || function() {}

    if (!exportedOutputPins[pin]) {
        return process.nextTick(function() {
            cb(new Error('Pin has not been exported for write'));
        });
    }

    value = (!!value && value !== '0') ? '1' : '0';

    debug('writing pin %d with value %s', pin, value);
    fs.writeFile(PATH + '/gpio' + pin + '/value', value, cb);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.rpi-gpio.read"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>read (channel, cb)](#apidoc.element.rpi-gpio.read)
- description and source-code
```javascript
read = function (channel, cb) {
    if (typeof cb !== 'function') {
        throw new Error('A callback must be provided')
    }

    var pin = getPinForCurrentMode(channel);

    if (!exportedInputPins[pin] && !exportedOutputPins[pin]) {
        return process.nextTick(function() {
            cb(new Error('Pin has not been exported'));
        });
    }

    fs.readFile(PATH + '/gpio' + pin + '/value', 'utf-8', function(err, data) {
        if (err) {
            return cb(err)
        }
        data = (data + '').trim() || '0';
        debug('read pin %s with value %s', pin, data);
        return cb(null, data === '1');
    });
}
```
- example usage
```shell
...
### Setup and read the value of a pin
'''js
var gpio = require('rpi-gpio');

gpio.setup(7, gpio.DIR_IN, readInput);

function readInput() {
    gpio.read(7, function(err, value) {
        console.log('The value is ' + value);
    });
}
'''

### Setup and write to a pin
'''js
...
```

#### <a name="apidoc.element.rpi-gpio.reset"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>reset ()](#apidoc.element.rpi-gpio.reset)
- description and source-code
```javascript
reset = function () {
    exportedOutputPins = {};
    exportedInputPins = {};
    this.removeAllListeners();

    currentPins = undefined;
    getPinForCurrentMode = getPinRpi;
    pollers = {}
}
```
- example usage
```shell
...
    currentPins = undefined;
    getPinForCurrentMode = getPinRpi;
    pollers = {}
};

// Init
EventEmitter.call(this);
this.reset();


// Private functions requring access to state
function setRaspberryVersion(cb) {
    if (currentPins) {
        return cb(null);
    }
...
```

#### <a name="apidoc.element.rpi-gpio.setMode"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>setMode (mode)](#apidoc.element.rpi-gpio.setMode)
- description and source-code
```javascript
setMode = function (mode) {
    if (mode === this.MODE_RPI) {
        getPinForCurrentMode = getPinRpi;
    } else if (mode === this.MODE_BCM) {
        getPinForCurrentMode = getPinBcm;
    } else {
        throw new Error('Cannot set invalid mode');
    }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.rpi-gpio.setup"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>setup (channel, direction, edge, onSetup)](#apidoc.element.rpi-gpio.setup)
- description and source-code
```javascript
setup = function (channel, direction, edge, onSetup) {
    if (arguments.length === 2 && typeof direction == 'function') {
        onSetup = direction;
        direction = this.DIR_OUT;
        edge = this.EDGE_NONE;
    } else if (arguments.length === 3 && typeof edge == 'function') {
        onSetup = edge;
        edge = this.EDGE_NONE;
    }

    channel = parseInt(channel)
    direction = direction || this.DIR_OUT;
    edge = edge || this.EDGE_NONE;
    onSetup = onSetup || function() {};

    if (typeof channel !== 'number') {
        return process.nextTick(function() {
            onSetup(new Error('Channel must be a number'));
        });
    }

    if (direction !== this.DIR_IN && direction !== this.DIR_OUT) {
        return process.nextTick(function() {
            onSetup(new Error('Cannot set invalid direction'));
        });
    }

    if ([
        this.EDGE_NONE,
        this.EDGE_RISING,
        this.EDGE_FALLING,
        this.EDGE_BOTH
    ].indexOf(edge) == -1) {
        return process.nextTick(function() {
            onSetup(new Error('Cannot set invalid edge'));
        });
    }

    var pinForSetup;
    async.waterfall([
        setRaspberryVersion,
        function(next) {
            pinForSetup = getPinForCurrentMode(channel);
            if (!pinForSetup) {
                return next(new Error('Channel ' + channel + ' does not map to a GPIO pin'));
            }
            debug('set up pin %d', pinForSetup);
            isExported(pinForSetup, next);
        },
        function(isExported, next) {
            if (isExported) {
                return unexportPin(pinForSetup, next);
            }
            return next(null);
        },
        function(next) {
            exportPin(pinForSetup, next);
        },
        function(next) {
            setEdge(pinForSetup, edge, next);
        },
        function(next) {
            if (direction === this.DIR_IN) {
                exportedInputPins[pinForSetup] = true;
            } else {
                exportedOutputPins[pinForSetup] = true;
            }

            setDirection(pinForSetup, direction, next);
        }.bind(this),
        function(next) {
            listen(channel, function(readChannel) {
                this.read(readChannel, function(err, value) {
                    if (err) {
                        debug(
                            'Error reading channel value after change, %d',
                            readChannel
                        );
                        return
                    }
                    debug('emitting change on channel %s with value %s', readChannel, value);
                    this.emit('change', readChannel, value);
                }.bind(this));
            }.bind(this));
            next()
        }.bind(this)
    ], onSetup);
}
```
- example usage
```shell
...

## Examples

### Setup and read the value of a pin
'''js
var gpio = require('rpi-gpio');

gpio.setup(7, gpio.DIR_IN, readInput);

function readInput() {
    gpio.read(7, function(err, value) {
        console.log('The value is ' + value);
    });
}
'''
...
```

#### <a name="apidoc.element.rpi-gpio.write"></a>[function <span class="apidocSignatureSpan">rpi-gpio.</span>write (channel, value, cb)](#apidoc.element.rpi-gpio.write)
- description and source-code
```javascript
write = function (channel, value, cb) {
    var pin = getPinForCurrentMode(channel);
    cb = cb || function() {}

    if (!exportedOutputPins[pin]) {
        return process.nextTick(function() {
            cb(new Error('Pin has not been exported for write'));
        });
    }

    value = (!!value && value !== '0') ? '1' : '0';

    debug('writing pin %d with value %s', pin, value);
    fs.writeFile(PATH + '/gpio' + pin + '/value', value, cb);
}
```
- example usage
```shell
...
### Setup and write to a pin
'''js
var gpio = require('rpi-gpio');

gpio.setup(7, gpio.DIR_OUT, write);

function write() {
    gpio.write(7, true, function(err) {
        if (err) throw err;
        console.log('Written to pin');
    });
}
'''

### Listen for changes on a pin
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
