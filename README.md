BME680 + Rust [![Build Status](https://travis-ci.org/marcelbuesing/bme680.svg?branch=master)](https://travis-ci.org/marcelbuesing/bme680)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fmarcelbuesing%2Fbme680.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fmarcelbuesing%2Fbme680?ref=badge_shield)
=============

This repository contains a pure Rust implementation for the [BME680](https://www.bosch-sensortec.com/bst/products/all_products/bme680) environmental sensor. The library can be used to read the gas, pressure, humidity and temperature sensors via I²C.

The library uses the [embedded-hal](https://github.com/japaric/embedded-hal) library to abstract reading and writing via I²C. In the examples you can find a demo how to use the library in Linux using the [linux-embedded-hal](https://github.com/japaric/linux-embedded-hal) implementation.

# Example getting started Linux

Determine the I2C device path

```
pi@raspberrypi:~ $ i2cdetect -y -l
i2c-1    i2c       bcm2835 I2C adapter             I2C adapter
```

Determine I2C-Address of sensor, `0x76` is the primary address, `0x77` is the secondary address.
If in doubt determine the address via the following command:

```
pi@raspberrypi:~ $ i2cdetect -y 1
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- --
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
30: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
70: -- -- -- -- -- -- 76
```

# Example Influx Client
The examples folder contains an example for a simple influx database client inserting collected values.
Below you may find examples of Chronograf graphs of an indoor measurement over a period of 30 days.

![Temperature Graph](examples/res/influx_temperature.png "Temperature measurement in C°")
![Humidity Graph](examples/res/influx_humidity.png "Humidity measurement in %")
![Air pressure Graph](examples/res/influx_pressure.png "Air pressure measurement in hPa")
![Gas resistance Graph](examples/res/influx_gas_resistance.png "Gas resistance measurement")

## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fmarcelbuesing%2Fbme680.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fmarcelbuesing%2Fbme680?ref=badge_large)