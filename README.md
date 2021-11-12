# Node SandBox Pi

## Install

```bash
npm install https://github.com/oleksandr-sovenko/node-sandboxpi
```
or
```bash
npm install https://github.com/oleksandr-sovenko/node-sandboxpi -g --unsafe
npm link node-sandboxpi # (optional) for each project where will be used 'node-sandboxpi'
```

## Examples

Example with led indicator (3.3v)

```javascript
const { GPIO } = require('node-sandboxpi');

GPIO.mode(30, GPIO.OUTPUT);
setInterval(function() {
   var state = GPIO.read(30);
 
   if (state === GPIO.HIGH)
      GPIO.write(30, GPIO.LOW);
   else
      GPIO.write(30, GPIO.HIGH);
}, 2000);
```

Example with sensor DS18B20 (5v)

```javascript
// DATA - PIN26

const { W1 } = require('node-sandboxpi');

var w1_dev = W1.getDevices(),
    sensor = W1.DS18B20(w1_dev[0].addr);
 
setInterval(function() {
    console.log(sensor.getTemperatureC());
    console.log(sensor.getTemperatureF());
}, 3000);
```
Example with sensor HC-SC04/SRO4M-2 (5v)

```javascript
const { HC_SC04 } = require('node-sandboxpi');

var hc_sc04 = HC_SC04(15, 16);
setInterval(function() {
    console.log(hc_sc04.getDistanceCM());
}, 1000);
```
Example with sensor BMP280 (3.3v)

```javascript
const { BMP280 } = require('node-sandboxpi'),

var bmp280 = BMP280();

setInterval(function() {
    console.log(bmp280.getData());
}, 1000);
```

## GPIO Buttons (pins)

1, 5, 8, 12, 14, 13

## GPIO Leds (pins, start off)

4, 5, 8, 11, 12, 13, 14
