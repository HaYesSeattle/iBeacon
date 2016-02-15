# iBeacon
test project for iBeacon

install cordova

add plugin: cordova plugin add https://github.com/petermetz/cordova-plugin-ibeacon.git

#####

Realtag iBeacon Firmware instructions:

Modify the parameters, Tag needs to be repower (power off and then open)
The work of the state, blue LED light D1 to signal broadcast interval frequency flicker
During of the work, you can press the S2 key to stop / start broadcasting (automatic broadcasts by default when the power is turned on)
The connection state is not broadcast, disconnection is restarted broadcasting
The connection can be read by Battery Service

Realtag iBeacon Firmware specifications:

1. The default iBeacon UUID: 0xE2C56DB5-DFFB-48D2-B060-D0F5A71096E0
2. iBeacons Parameters:
0xFFA0 -> 0xFFB0 Read/Write – Match password
0xFFA0 -> 0xFFB1 Read/Write – Major ID + Minor ID
0xFFA0 -> 0xFFB2 Read/Write – iBeacon UUID
0xFFA0 -> 0xFFB3 Read/Write – Broadcast interval
0xFFA0 -> 0xFFB4 Read/Write – The device ID
0xFFA0 -> 0xFFB5 Read/Write – Deployment model
0xFFA0 -> 0xFFB8 Read/Write – Tx power
0x180F -> 0x2A19 Read/Notify – Battery life
3. Support OAD, online upgrade firmware

Realtag iBeacon API Description:

Service UUID: 0xFFA0
0xFFB0: Pairing code (Read / Write)
Ex: 000000 (default 000000=without connection password)
0xFFB1: Major + Minor ID (Read / Write)
Ex: 0x01020304 (0x0102=Major ID. 0X0304=Minor ID)
0xFFB2: iBeacons UUID (Read / Write)
Ex: 0xE2C56DB5-DFFB-48D2-B060-DOF5A71096E0 (not recommended to modify)
0xFFB3: Advertising Interval (Read / Write)
Ex: 0x05 (broadcast interval is integer times, the default 100ms: 0x05=500ms)
Service UUID: 0xFFA0
0xFFB4: device ID (Read / Write)
Ex: iBeacons#
The 0xFFB5: deployment model (Read / Write)
Ex: write 0x00 into the deployment model (0x01: non deployment model of the default value)
The 0xFFB6: sensor MPU6050 data (Realtag Sensor)
Ex: HEX 0xA0009C02983E40F7FDFFBC00FFFF
The 0xFFB7: sensor BMP180 data (Realtag sensor)
Ex: HEX 0x16010000CA890100
0xFFB8: TX Power (Read / Write)
Ex: 0xC5 (default:0xC5. TX Power=-59)

Realtag Sensor-MPU6050 Data output:

MPU6050 raw data output (7)
XYZ acceleration sensor: ax, ay, AZ
Temperature: aTemp
Angular velocity of XYX: gx.gy.gz
Each value is 2 bytes (Big Endian model)
Ex: HEX0x0009C02983E40F7FDFFBC00FFFF
Ax= 0x 00 A0/ay= Ox 02 9C
Az= Ox 3E 98/
ATemp= Ox F7 40
Gx= Ox FF FD/gy 40= Ox OO BC
Gz= Ox FF FF

Realtag Sensor-BMP180 Data output:

BMP180 data output (temperature and pressure)
Each value is 4 bytes (Big Endian model)
Ex: HEX 0x16010000CA890100
Temperature= 0x 00000116= 278 X 0,1= 27.8 °C
Pressure= Ox 000189CA= 100810 panel
