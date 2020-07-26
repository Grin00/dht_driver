# DHT sensor API
## Introduction
This package contains the DHT teperature and humidity sensor driver (sensor API)

The sensor driver package includes dht_driver.h and dht_driver.c files.


## Integration details
* Integrate dht_driver.h and dht_driver.c in to the project.
* Include the dht_driver.h file in your code like below.
``` c
#include "dht_driver.h"
```

## File information
* dht_driver.h : This header file contains the declarations of the sensor driver APIs.
* dht_driver.c : This source file contains the definitions of the sensor driver APIs.

## Supported sensors
* DHT11
* DHT12
* DHT21
* DHT22

## Usage guide
### Initializing the sensor
To initialize the sensor, user need to create a sensor structure. User can do this by 
creating an instance of the structure dht_sensor_t. After creating the device strcuture, user 
need to fill in the various parameters as shown below.

#### Example of initialization for DHT22
``` c
dht_sensor_t sensor1 = {
    .type = DHT_22,
    .intrf = {
        .pin_init = user_pin_init,
        .pin_set = user_pin_set,
        .pin_read = user_pin_read,
        .delay_us = user_delay_us
}
```
#### Example sensor reading
``` c
//! Initialization of type and interface
dht_err_t rslt;
dht_sensor_t sensor1 = {
    .type = DHT_22,
    .intrf = {
        .pin_init = user_pin_init,
        .pin_set = user_pin_set,
        .pin_read = user_pin_read,
        .delay_us = user_delay_us
}

rslt = dht_read(&sensor1);

//! Output sensor's values
printf("Temperature: %.2f \r\n", sensor1.temperature);
printf("Humidity: %.2f \r\n", sensor1.humidity);
printf("Status: %s \r\n", sensor1.status == DHT_OK ? "DHT_OK" :
        sensor1.status == DHT_TIMEOUT ? "DHT_TIMEOUT" :
        sensor1.status == DHT_CRC_ERR ? "DHT_CRC_ERR" :
        "DHT_INVALID_ARG");
printf("-----------------------------\r\n");

```
#### Output
```
Temperature: 25.70 
Humidity: 32.00 
Status: DHT_OK 
-----------------------------
```
## Contributing
Pull requests are welcome. For major changes, please open an issue first to
discuss what you would like to change.

Please make sure to update tests as appropriate.
