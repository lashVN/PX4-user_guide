# 모듈 참조: 드라이버
하위 카테고리:
- [관성 센서](modules_driver_imu.md)
- [거리 센서](modules_driver_distance_sensor.md)
- [Ins](modules_driver_ins.md)
- [항속 센서](modules_driver_airspeed_sensor.md)
- [기압계](modules_driver_baro.md)
- [Transponder](modules_driver_transponder.md)
- [Rpm Sensor](modules_driver_rpm_sensor.md)
- [Optical Flow](modules_driver_optical_flow.md)
- [Magnetometer](modules_driver_magnetometer.md)

## MCP23009
Source: [drivers/gpio/mcp23009](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/gpio/mcp23009)

<a id="MCP23009_usage"></a>

### 사용법
```
MCP23009 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 37
     [-D <val>]  Direction
                 default: 0
     [-O <val>]  Output
                 default: 0
     [-P <val>]  Pullups
                 default: 0
     [-U <val>]  Update Interval [ms]
                 default: 0

   stop

   status        print status info
```
## adc
소스: [drivers/adc/board_adc](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/adc/board_adc)


### 설명
ADC 드라이버


<a id="adc_usage"></a>

### 사용법
```
adc <command> [arguments...]
 Commands:
   start

   test
     [-n]        Do not publish ADC report, only system power

   stop

   status        print status info
```
## ads1115
소스: [drivers/adc/ads1115](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/adc/ads1115)


### 설명

Driver to enable an external [ADS1115](https://www.adafruit.com/product/1085) ADC connected via I2C.

The driver is included by default in firmware for boards that do not have an internal analog to digital converter, such as [PilotPi](../flight_controller/raspberry_pi_pilotpi.md) or [CUAV Nora](../flight_controller/cuav_nora.md) (search for `CONFIG_DRIVERS_ADC_ADS1115` in board configuration files).

It is enabled/disabled using the [ADC_ADS1115_EN](../advanced_config/parameter_reference.md#ADC_ADS1115_EN) parameter, and is disabled by default. If enabled, internal ADCs are not used.


<a id="ads1115_usage"></a>

### 사용법
```
ads1115 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 72

   stop

   status        print status info
```
## atxxxx
소스: [drivers/osd/atxxxx](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/osd/atxxxx)


### 설명
예를 들어 OmnibusF4SD 보드에 장착된 ATXXXX 칩용 OSD 드라이버.

OSD_ATXXXX_CFG 매개변수로 활성화합니다.

<a id="atxxxx_usage"></a>

### 사용법
```
atxxxx <command> [arguments...]
 Commands:
   start
     [-s]        Internal SPI bus(es)
     [-S]        External SPI bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-c <val>]  chip-select index (for external SPI)
                 default: 1
     [-m <val>]  SPI mode
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)

   stop

   status        print status info
```
## batmon
소스: [drivers/smart_battery/batmon](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/smart_battery/batmon)


### 설명
BatMon 지원 스마트 배터리와 SMBUS 통신용 드라이버 설정/사용 정보: https://rotoye.com/batmon-tutorial/
### 예
주소 0x0B에서 시작하려면 버스 4에서
```
batmon start -X -a 11 -b 4
```


<a id="batmon_usage"></a>

### 사용법
```
batmon <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 11

   man_info      Prints manufacturer info.

   suspend       Suspends the driver from rescheduling the cycle.

   resume        Resumes the driver from suspension.

   stop

   status        print status info
```
## batt_smbus
소스: [drivers/batt_smbus](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/batt_smbus)


### 설명
BQ40Z50 연료 게이지 IC용 스마트 배터리 드라이버.

### 예
매개변수를 설정하기 위해 플래시에 쓰기. 주소, number_of_bytes, byte0, ..., byteN
```
batt_smbus -X write_flash 19069 2 27 0
```


<a id="batt_smbus_usage"></a>

### 사용법
```
batt_smbus <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 11

   man_info      Prints manufacturer info.

   unseal        Unseals the devices flash memory to enable write_flash
                 commands.

   seal          Seals the devices flash memory to disable write_flash commands.

   suspend       Suspends the driver from rescheduling the cycle.

   resume        Resumes the driver from suspension.

   write_flash   Writes to flash. The device must first be unsealed with the
                 unseal command.
     [address]   The address to start writing.
     [number of bytes] Number of bytes to send.
     [data[0]...data[n]] One byte of data at a time separated by spaces.

   stop

   status        print status info
```
## bst
소스: [drivers/telemetry/bst](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/telemetry/bst)

<a id="bst_usage"></a>

### 사용법
```
bst <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 118

   stop

   status        print status info
```
## crsf_rc
Source: [drivers/rc/crsf_rc](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/rc/crsf_rc)


### 설명
This module parses the CRSF RC uplink protocol and generates CRSF downlink telemetry data


<a id="crsf_rc_usage"></a>

### 사용법
```
crsf_rc <command> [arguments...]
 Commands:
   start
     [-d <val>]  RC device
                 values: <file:dev>, default: /dev/ttyS3

   stop

   status        print status info
```
## dshot
소스: [drivers/dshot](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/dshot)


### 설명
이것은 DShot 출력 드라이버입니다. fmu 드라이버와 유사하며, PWM 대신 ESC 통신 프로토콜로 DShot을 사용하기 위하여 사용할 수 있습니다.

On startup, the module tries to occupy all available pins for DShot output. It skips all pins already in use (e.g. by a camera trigger module).

모터 1 영구 역회전 :
- DShot150, DShot300, DShot600, DShot1200
- 별도의 UART를 통한 텔레메트리와 esc_status 메시지로 게시
- CLI를 통해 DShot 명령 보내기

### 예
Permanently reverse motor 1:
```
dshot reverse -m 1
dshot save -m 1
```
After saving, the reversed direction will be regarded as the normal one. So to reverse again repeat the same commands.

<a id="dshot_usage"></a>

### 사용법
```
dshot <command> [arguments...]
 Commands:
   start         Start the task (without any mode set, use any of the mode_*
                 cmds)

 All of the mode_* commands will start the module if not running already

   mode_gpio

   mode_pwm      Select all available pins as PWM

   mode_pwm14

   mode_pwm12

   mode_pwm8

   mode_pwm6

   mode_pwm5

   mode_pwm5cap1

   mode_pwm4

   mode_pwm4cap1

   mode_pwm4cap2

   mode_pwm3

   mode_pwm3cap1

   mode_pwm2

   mode_pwm2cap2

   mode_pwm1

   telemetry     Enable Telemetry on a UART
     <device>    UART device

   reverse       Reverse motor direction
     [-m <val>]  Motor index (1-based, default=all)

   normal        Normal motor direction
     [-m <val>]  Motor index (1-based, default=all)

   save          Save current settings
     [-m <val>]  Motor index (1-based, default=all)

   3d_on         Enable 3D mode
     [-m <val>]  Motor index (1-based, default=all)

   3d_off        Disable 3D mode
     [-m <val>]  Motor index (1-based, default=all)

   beep1         Send Beep pattern 1
     [-m <val>]  Motor index (1-based, default=all)

   beep2         Send Beep pattern 2
     [-m <val>]  Motor index (1-based, default=all)

   beep3         Send Beep pattern 3
     [-m <val>]  Motor index (1-based, default=all)

   beep4         Send Beep pattern 4
     [-m <val>]  Motor index (1-based, default=all)

   beep5         Send Beep pattern 5
     [-m <val>]  Motor index (1-based, default=all)

   esc_info      Request ESC information
     -m <val>    Motor index (1-based)

   stop

   status        print status info
```
## fake_gps
소스: [examples/fake_imu](https://github.com/PX4/PX4-Autopilot/tree/master/src/examples/fake_imu)


### 설명


<a id="fake_gps_usage"></a>

### 사용법
```
fake_gps <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## fake_imu
소스: [examples/fake_magnetometer](https://github.com/PX4/PX4-Autopilot/tree/master/src/examples/fake_magnetometer)


### 설명


<a id="fake_imu_usage"></a>

### 사용법
```
fake_imu <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## fake_magnetometer
Source: [examples/fake_magnetometer](https://github.com/PX4/PX4-Autopilot/tree/master/src/examples/fake_magnetometer)


### 설명
Publish the earth magnetic field as a fake magnetometer (sensor_mag). Requires vehicle_attitude and vehicle_gps_position.

<a id="fake_magnetometer_usage"></a>

### 사용법
```
fake_magnetometer <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## ft_technologies_serial
Source: [drivers/wind_sensor/ft_technologies](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/wind_sensor/ft_technologies)


### 설명

Serial bus driver for the FT Technologies Digital Wind Sensor FT742. This driver is required to operate alongside a RS485 to UART signal transfer module.

Most boards are configured to enable/start the driver on a specified UART using the SENS_FTX_CFG parameter.

### 예

Attempt to start driver on a specified serial device.
```
ft_technologies_serial start -d /dev/ttyS1
```
Stop driver
```
ft_technologies_serial stop
```

<a id="ft_technologies_serial_usage"></a>

### Usage
```
ft_technologies_serial <command> [arguments...]
 Commands:
   start         Start driver
     -d <val>    Serial device

   stop          Stop driver
```
## gimbal
Source: [modules/gimbal](https://github.com/PX4/PX4-Autopilot/tree/master/src/modules/gimbal)


### Description
Mount/gimbal Gimbal control driver. It maps several different input methods (eg. RC or MAVLink) to a configured output (eg. AUX channels or MAVLink).

Documentation how to use it is on the [gimbal_control](https://docs.px4.io/main/en/advanced/gimbal_control.html) page.

### 예
Test the output by setting a angles (all omitted axes are set to 0):
```
gimbal test pitch -45 yaw 30
```

<a id="gimbal_usage"></a>

### Usage
```
gimbal <command> [arguments...]
 Commands:
   start

   status

   primary-control Set who is in control of gimbal
     <sysid> <compid> MAVLink system ID and MAVLink component ID

   test          Test the output: set a fixed angle for one or multiple axes
                 (gimbal must be running)
     roll|pitch|yaw <angle> Specify an axis and an angle in degrees

   stop

   status        print status info
```
## gps
Source: [drivers/gps](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/gps)


### Description
GPS driver module that handles the communication with the device and publishes the position via uORB. It supports multiple protocols (device vendors) and by default automatically selects the correct one.

The module supports a secondary GPS device, specified via `-e` parameter. The position will be published on the second uORB topic instance, but it's currently not used by the rest of the system (however the data will be logged, so that it can be used for comparisons).

### Implementation
There is a thread for each device polling for data. The GPS protocol classes are implemented with callbacks so that they can be used in other projects as well (eg. QGroundControl uses them too).

### 예

Starting 2 GPS devices (the main GPS on /dev/ttyS3 and the secondary on /dev/ttyS4):
```
gps start -d /dev/ttyS3 -e /dev/ttyS4
```

Initiate warm restart of GPS device
```
gps reset warm
```

<a id="gps_usage"></a>

### 설명
```
gps <command> [arguments...]
 Commands:
   start
     [-d <val>]  GPS device
                 values: <file:dev>, default: /dev/ttyS3
     [-b <val>]  Baudrate (can also be p:<param_name>)
                 default: 0
     [-e <val>]  Optional secondary GPS device
                 values: <file:dev>
     [-g <val>]  Baudrate (secondary GPS, can also be p:<param_name>)
                 default: 0
     [-i <val>]  GPS interface
                 values: spi|uart, default: uart
     [-j <val>]  secondary GPS interface
                 values: spi|uart, default: uart
     [-p <val>]  GPS Protocol (default=auto select)
                 values: ubx|mtk|ash|eml|fem|nmea

   stop

   status        print status info

   reset         Reset GPS device
     cold|warm|hot Specify reset type
```
## gz_bridge
Source: [modules/simulation/gz_bridge](https://github.com/PX4/PX4-Autopilot/tree/main/src/modules/simulation/gz_bridge)


### 예


<a id="gz_bridge_usage"></a>

### Usage
```
gz_bridge <command> [arguments...]
 Commands:
   start
     -m <val>    Fuel model name
     -p <val>    Model Pose
     -n <val>    Model name
     -i <val>    PX4 instance
     [-w <val>]  World name

   stop

   status        print status info
```
## ina220
Source: [drivers/power_monitor/ina220](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/power_monitor/ina220)


### Description
Driver for the INA220 power monitor.

Multiple instances of this driver can run simultaneously, if each instance has a separate bus OR I2C address.

For example, one instance can run on Bus 2, address 0x41, and one can run on Bus 2, address 0x43.

If the INA220 module is not powered, then by default, initialization of the driver will fail. To change this, use the -f flag. If this flag is set, then if initialization fails, the driver will keep trying to initialize again every 0.5 seconds. With this flag set, you can plug in a battery after the driver starts, and it will work. Without this flag set, the battery must be plugged in before starting the driver.


<a id="ina220_usage"></a>

### Usage
```
ina220 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 65
     [-k]        if initialization (probing) fails, keep retrying periodically
     [-t <val>]  battery index for calibration values (1 or 3)
                 default: 1
     [-T <val>]  Type
                 values: VBATT|VREG, default: VBATT

   stop

   status        print status info
```
## ina226
Source: [drivers/power_monitor/ina226](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/power_monitor/ina226)


### Description
Driver for the INA226 power monitor.

Multiple instances of this driver can run simultaneously, if each instance has a separate bus OR I2C address.

For example, one instance can run on Bus 2, address 0x41, and one can run on Bus 2, address 0x43.

If the INA226 module is not powered, then by default, initialization of the driver will fail. To change this, use the -f flag. If this flag is set, then if initialization fails, the driver will keep trying to initialize again every 0.5 seconds. With this flag set, you can plug in a battery after the driver starts, and it will work. Without this flag set, the battery must be plugged in before starting the driver.


<a id="ina226_usage"></a>

### Usage
```
ina226 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 65
     [-k]        if initialization (probing) fails, keep retrying periodically
     [-t <val>]  battery index for calibration values (1 or 3)
                 default: 1

   stop

   status        print status info
```
## ina228
Source: [drivers/power_monitor/ina228](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/power_monitor/ina228)


### Description
Driver for the INA228 power monitor.

Multiple instances of this driver can run simultaneously, if each instance has a separate bus OR I2C address.

For example, one instance can run on Bus 2, address 0x45, and one can run on Bus 2, address 0x45.

If the INA228 module is not powered, then by default, initialization of the driver will fail. To change this, use the -f flag. If this flag is set, then if initialization fails, the driver will keep trying to initialize again every 0.5 seconds. With this flag set, you can plug in a battery after the driver starts, and it will work. Without this flag set, the battery must be plugged in before starting the driver.


<a id="ina228_usage"></a>

### Usage
```
ina228 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 69
     [-k]        if initialization (probing) fails, keep retrying periodically
     [-t <val>]  battery index for calibration values (1 or 3)
                 default: 1

   stop

   status        print status info
```
## ina238
Source: [drivers/power_monitor/ina238](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/power_monitor/ina238)


### Description
Driver for the INA238 power monitor.

Multiple instances of this driver can run simultaneously, if each instance has a separate bus OR I2C address.

For example, one instance can run on Bus 2, address 0x45, and one can run on Bus 2, address 0x45.

If the INA238 module is not powered, then by default, initialization of the driver will fail. To change this, use the -f flag. If this flag is set, then if initialization fails, the driver will keep trying to initialize again every 0.5 seconds. With this flag set, you can plug in a battery after the driver starts, and it will work. Without this flag set, the battery must be plugged in before starting the driver.


<a id="ina238_usage"></a>

### 사용법
```
ina238 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 69
     [-k]        if initialization (probing) fails, keep retrying periodically
     [-t <val>]  battery index for calibration values (1 or 3)
                 default: 1

   stop

   status        print status info
```
## iridiumsbd
Source: [drivers/telemetry/iridiumsbd](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/telemetry/iridiumsbd)


### Description
IridiumSBD driver.

Creates a virtual serial port that another module can use for communication (e.g. mavlink).

<a id="iridiumsbd_usage"></a>

### Usage
```
iridiumsbd <command> [arguments...]
 Commands:
   start
     -d <val>    Serial device
                 values: <file:dev>
     [-v]        Enable verbose output

   test
     [s|read|AT <cmd>] Test command

   stop

   status        print status info
```
## irlock
Source: [drivers/irlock](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/irlock)

<a id="irlock_usage"></a>

### Usage
```
irlock <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 84

   stop

   status        print status info
```
## linux_pwm_out
Source: [drivers/linux_pwm_out](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/linux_pwm_out)


### 설명
Linux PWM output driver with board-specific backend implementation.

<a id="linux_pwm_out_usage"></a>

### Usage
```
linux_pwm_out <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## lsm303agr
Source: [drivers/magnetometer/lsm303agr](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/magnetometer/lsm303agr)

<a id="lsm303agr_usage"></a>

### 사용법
```
lsm303agr <command> [arguments...]
 Commands:
   start
     [-s]        Internal SPI bus(es)
     [-S]        External SPI bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-c <val>]  chip-select pin (for internal SPI) or index (for external SPI)
     [-m <val>]  SPI mode
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-R <val>]  Rotation
                 default: 0

   stop

   status        print status info
```
## msp_osd
Source: [drivers/osd/msp_osd](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/osd/msp_osd)


### 설명
MSP telemetry streamer

### Implementation
Converts uORB messages to MSP telemetry packets

### 예
CLI usage example:
```
msp_osd
```


<a id="msp_osd_usage"></a>

### Usage
```
msp_osd <command> [arguments...]
 Commands:
   stop

   status        print status info
```
## newpixel
Source: [drivers/lights/neopixel](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/lights/neopixel)


### 설명
This module is responsible for driving interfasing to the Neopixel Serial LED

### 예
It is typically started with:
```
neopixel -n 8
```
To drive all available leds.

<a id="newpixel_usage"></a>

### Usage
```
newpixel <command> [arguments...]
 Commands:
   stop

   status        print status info
```
## paa3905
Source: [drivers/optical_flow/paa3905](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/optical_flow/paa3905)

<a id="paa3905_usage"></a>

### 사용법
```
paa3905 <command> [arguments...]
 Commands:
   start
     [-s]        Internal SPI bus(es)
     [-S]        External SPI bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-c <val>]  chip-select pin (for internal SPI) or index (for external SPI)
     [-m <val>]  SPI mode
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-Y <val>]  custom yaw rotation (degrees)
                 default: 0

   stop

   status        print status info
```
## paw3902
Source: [drivers/optical_flow/paw3902](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/optical_flow/paw3902)

<a id="paw3902_usage"></a>

### Usage
```
paw3902 <command> [arguments...]
 Commands:
   start
     [-s]        Internal SPI bus(es)
     [-S]        External SPI bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-c <val>]  chip-select pin (for internal SPI) or index (for external SPI)
     [-m <val>]  SPI mode
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-Y <val>]  custom yaw rotation (degrees)
                 default: 0

   stop

   status        print status info
```
## pca9685_pwm_out
Source: [drivers/pca9685_pwm_out](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/pca9685_pwm_out)


### 설명
This is a PCA9685 PWM output driver.

It runs on I2C workqueue which is asynchronous with FC control loop, fetching the latest mixing result and write them to PCA9685 at its scheduling ticks.

It can do full 12bits output as duty-cycle mode, while also able to output precious pulse width that can be accepted by most ESCs and servos.

### 예
It is typically started with:
```
pca9685_pwm_out start -a 0x40 -b 1
```


<a id="pca9685_pwm_out_usage"></a>

### 사용법
```
pca9685_pwm_out <command> [arguments...]
 Commands:
   start         Start the task
     [-a <val>]  7-bits I2C address of PCA9685
                 values: <addr>, default: 0x40
     [-b <val>]  bus that pca9685 is connected to
                 default: 1

   stop

   status        print status info
```
## pm_selector_auterion
Source: [drivers/power_monitor/pm_selector_auterion](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/power_monitor/pm_selector_auterion)


### 설명
Driver for starting and auto-detecting different power monitors.


<a id="pm_selector_auterion_usage"></a>

### 사용법
```
pm_selector_auterion <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## pmw3901
Source: [drivers/optical_flow/pmw3901](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/optical_flow/pmw3901)

<a id="pmw3901_usage"></a>

### 사용법
```
pmw3901 <command> [arguments...]
 Commands:
   start
     [-s]        Internal SPI bus(es)
     [-S]        External SPI bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-c <val>]  chip-select pin (for internal SPI) or index (for external SPI)
     [-m <val>]  SPI mode
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-R <val>]  Rotation
                 default: 0

   stop

   status        print status info
```
## pps_capture
Source: [drivers/pps_capture](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/pps_capture)


### 설명
This implements capturing PPS information from the GNSS module and calculates the drift between PPS and Real-time clock.


<a id="pps_capture_usage"></a>

### 사용법
```
pps_capture <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## pwm_out
Source: [drivers/pwm_out](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/pwm_out)


### 설명
This module is responsible for driving the output pins. For boards without a separate IO chip (eg. Pixracer), it uses the main channels. On boards with an IO chip (eg. Pixhawk), it uses the AUX channels, and the px4io driver is used for main ones.


<a id="pwm_out_usage"></a>

### 사용법
```
pwm_out <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## pwm_out_sim
Source: [modules/simulation/pwm_out_sim](https://github.com/PX4/PX4-Autopilot/tree/main/src/modules/simulation/pwm_out_sim)


### 설명
Driver for simulated PWM outputs.

Its only function is to take `actuator_control` uORB messages, mix them with any loaded mixer and output the result to the `actuator_output` uORB topic.

It is used in SITL and HITL.


<a id="pwm_out_sim_usage"></a>

### 사용법
```
pwm_out_sim <command> [arguments...]
 Commands:
   start         Start the module
     [-m <val>]  Mode
                 values: hil|sim, default: sim

   stop

   status        print status info
```
## px4flow
Source: [drivers/optical_flow/px4flow](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/optical_flow/px4flow)

<a id="px4flow_usage"></a>

### 사용법
```
px4flow <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 66

   stop

   status        print status info
```
## px4io
Source: [drivers/px4io](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/px4io)


### 설명
Output driver communicating with the IO co-processor.

<a id="px4io_usage"></a>

### 사용법
```
px4io <command> [arguments...]
 Commands:
   start

   checkcrc      Check CRC for a firmware file against current code on IO
     <filename>  Firmware file

   update        Update IO firmware
     [<filename>] Firmware file

   debug         set IO debug level
     <debug_level> 0=disabled, 9=max verbosity

   bind          DSM bind
     dsm2|dsmx|dsmx8 protocol

   sbus1_out     enable sbus1 out

   sbus2_out     enable sbus2 out

   supported     Returns 0 if px4io is supported

   test_fmu_fail test: turn off IO updates

   test_fmu_ok   re-enable IO updates

   stop

   status        print status info
```
## rc_input
Source: [drivers/rc_input](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/rc_input)


### 설명
This module does the RC input parsing and auto-selecting the method. Supported methods are:
- PPM
- SBUS
- DSM
- SUMD
- ST24
- TBS Crossfire (CRSF)


<a id="rc_input_usage"></a>

### 사용법
```
rc_input <command> [arguments...]
 Commands:
   start
     [-d <val>]  RC device
                 values: <file:dev>, default: /dev/ttyS3

   bind          Send a DSM bind command (module must be running)

   stop

   status        print status info
```
## rgbled
Source: [drivers/lights/rgbled_ncp5623c](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/lights/rgbled_ncp5623c)

<a id="rgbled_usage"></a>

### 사용법
```
rgbled <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 57
     [-o <val>]  RGB PWM Assignment
                 default: 123

   stop

   status        print status info
```
## rgbled_is31fl3195
Source: [drivers/lights/rgbled_is31fl3195](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/lights/rgbled_is31fl3195)

<a id="rgbled_is31fl3195_usage"></a>

### 사용법
```
rgbled_is31fl3195 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 84
     [-o <val>]  RGB PWM Assignment
                 default: 123
     [-i <val>]  Current Band
                 default: 0.5

   stop

   status        print status info
```
## rgbled_lp5562
Source: [drivers/lights/rgbled_lp5562](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/lights/rgbled_lp5562)


### 설명
Driver for [LP5562](https://www.ti.com/product/LP5562) LED driver connected via I2C.

This used in some GPS modules by Holybro for [PX4 status notification](../getting_started/led_meanings.md)

The driver is included by default in firmware (KConfig key DRIVERS_LIGHTS_RGBLED_LP5562) and is always enabled.

<a id="rgbled_lp5562_usage"></a>

### 사용법
```
rgbled_lp5562 <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 48
     [-u <val>]  Current in mA
                 default: 17.5

   stop

   status        print status info
```
## roboclaw
Source: [drivers/roboclaw](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/roboclaw)


### 설명

This driver communicates over UART with the [Roboclaw motor driver](https://www.basicmicro.com/motor-controller). It performs two tasks:

 - Control the motors based on the OutputModuleInterface.
 - Read the wheel encoders and publish the raw data in the `wheel_encoders` uORB topic

In order to use this driver, the Roboclaw should be put into Packet Serial mode (see the linked documentation), and your flight controller's UART port should be connected to the Roboclaw as shown in the documentation. The driver needs to be enabled using the parameter `RBCLW_SER_CFG`, the baudrate needs to be set correctly and the address `RBCLW_ADDRESS` needs to match the ESC configuration.

The command to start this driver is: `$ roboclaw start <UART device> <baud rate>`

<a id="roboclaw_usage"></a>

### 사용법
```
roboclaw <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## safety_button
Source: [drivers/safety_button](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/safety_button)


### 설명
This module is responsible for the safety button. Pressing the safety button 3 times quickly will trigger a GCS pairing request.


<a id="safety_button_usage"></a>

### 사용법
```
safety_button <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## sht3x
Source: [drivers/hygrometer/sht3x](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/hygrometer/sht3x)


### 설명
SHT3x Temperature and Humidity Sensor Driver by Senserion.

### 예
CLI usage example:
```
sht3x start -X
```
  Start the sensor driver on the external bus

```
sht3x status
```
  Print driver status

```
sht3x values
```
  Print last measured values

```
sht3x reset
```
  Reinitialize senzor, reset flags


<a id="sht3x_usage"></a>

### Usage
```
sht3x <command> [arguments...]
 Commands:
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 68
     [-k]        if initialization (probing) fails, keep retrying periodically

   stop

   status        print status info

   values        Print actual data

   reset         Reinitialize sensor
```
## tap_esc
Source: [drivers/tap_esc](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/tap_esc)


### Description

This module controls the TAP_ESC hardware via UART. It listens on the actuator_controls topics, does the mixing and writes the PWM outputs.

### Implementation

Currently the module is implemented as a threaded version only, meaning that it runs in its own thread instead of on the work queue.

### Example

The module is typically started with:

```
tap_esc start -d /dev/ttyS2 -n <1-8>
```

<a id="tap_esc_usage"></a>

### 사용법
```
tap_esc <command> [arguments...]
 Commands:
   start         Start the task
     [-d <val>]  Device used to talk to ESCs
                 values: <device>
     [-n <val>]  Number of ESCs
                 default: 4
```
## tone_alarm
Source: [drivers/tone_alarm](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/tone_alarm)


### 설명
This module is responsible for the tone alarm.


<a id="tone_alarm_usage"></a>

### 사용법
```
tone_alarm <command> [arguments...]
 Commands:
   start

   stop

   status        print status info
```
## uwb
Source: [drivers/uwb/uwb_sr150](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/uwb/uwb_sr150)


### 설명

Driver for NXP UWB_SR150 UWB positioning system. This driver publishes a `uwb_distance` message whenever the UWB_SR150 has a position measurement available.

### Example

Start the driver with a given device:

```
uwb start -d /dev/ttyS2
```

<a id="uwb_usage"></a>

### 사용법
```
uwb <command> [arguments...]
 Commands:
   start
     -d <val>    Name of device for serial communication with UWB
                 values: <file:dev>
     -b <val>    Baudrate for serial communication
                 values: <int>

   stop

   status
```
## voxl2_io
Source: [drivers/voxl2_io](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/voxl2_io)


### Description
This module is responsible for driving the output pins. For boards without a separate IO chip (eg. Pixracer), it uses the main channels. On boards with an IO chip (eg. Pixhawk), it uses the AUX channels, and the px4io driver is used for main ones.


<a id="voxl2_io_usage"></a>

### 사용법
```
voxl2_io <command> [arguments...]
 Commands:
   start         Start the task
     -v          Verbose messages
     -d          Disable PWM
     -e          Disable RC
     -p <val>    UART port

   calibrate_escs Calibrate ESCs min/max range

   calibrate_escs Calibrate ESCs min/max range

   pwm           Open-Loop PWM test control request
     -c <val>    PWM OUTPUT Channel, 0-3
     -r <val>    Duty Cycle value, 0 to 800
     -n <val>    Command repeat count, 0 to INT_MAX
     -t <val>    Delay between repeated commands (microseconds), 0 to INT_MAX

   stop

   status        print status info
```
## voxl_esc
Source: [drivers/actuators/voxl_esc](https://github.com/PX4/PX4-Autopilot/tree/main/src/drivers/actuators/voxl_esc)


### Description
This module is responsible for...

### Implementation
By default the module runs on a work queue with a callback on the uORB actuator_controls topic.

### Examples
It is typically started with:
```
todo
```


<a id="voxl_esc_usage"></a>

### Usage
```
voxl_esc <command> [arguments...]
 Commands:
   start         Start the task

   reset         Send reset request to ESC
     -i <val>    ESC ID, 0-3

   version       Send version request to ESC
     -i <val>    ESC ID, 0-3

   version-ext   Send extended version request to ESC
     -i <val>    ESC ID, 0-3

   rpm           Closed-Loop RPM test control request
     -i <val>    ESC ID, 0-3
     -r <val>    RPM, -32,768 to 32,768
     -n <val>    Command repeat count, 0 to INT_MAX
     -t <val>    Delay between repeated commands (microseconds), 0 to INT_MAX

   pwm           Open-Loop PWM test control request
     -i <val>    ESC ID, 0-3
     -r <val>    Duty Cycle value, 0 to 800
     -n <val>    Command repeat count, 0 to INT_MAX
     -t <val>    Delay between repeated commands (microseconds), 0 to INT_MAX

   tone          Send tone generation request to ESC
     -i <val>    ESC ID, 0-3
     -p <val>    Period of sound, inverse frequency, 0-255
     -d <val>    Duration of the sound, 0-255, 1LSB = 13ms
     -v <val>    Power (volume) of sound, 0-100

   led           Send LED control request
     -l <val>    Bitmask 0x0FFF (12 bits) - ESC0 (RGB) ESC1 (RGB) ESC2 (RGB)
                 ESC3 (RGB)

   stop

   status        print status info
```
## voxlpm
Source: [drivers/power_monitor/voxlpm](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/power_monitor/voxlpm)

<a id="voxlpm_usage"></a>

### Usage
```
voxlpm [arguments...]
   start
     [-I]        Internal I2C bus(es)
     [-X]        External I2C bus(es)
     [-b <val>]  board-specific bus (default=all) (external SPI: n-th bus
                 (default=1))
     [-f <val>]  bus frequency in kHz
     [-q]        quiet startup (no message if no device found)
     [-a <val>]  I2C address
                 default: 68
     [-T <val>]  Type
                 values: VBATT|P5VDC|P12VDC, default: VBATT
     [-k]        if initialization (probing) fails, keep retrying periodically

   stop

   status        print status info
```
## zenoh
Source: [modules/zenoh](https://github.com/PX4/PX4-Autopilot/tree/main/src/modules/zenoh)


### Description

Zenoh demo bridge

<a id="zenoh_usage"></a>

### Usage
```
zenoh <command> [arguments...]
 Commands:
   start

   stop

   status

   config
```
