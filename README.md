1. add user with low privilege 2 (user need to execute commands: show interface transceiver and terminal length 0)
2. login to switch use this username and do next:
  2.1 terminal length 0
  2.2 show interface transceiver detail
Example output:
                              High Alarm  High Warn  Low Warn   Low Alarm
          Temperature         Threshold   Threshold  Threshold  Threshold
Port       (Celsius)          (Celsius)   (Celsius)  (Celsius)  (Celsius)
--------- ------------------  ----------  ---------  ---------  ---------
Te1/1/4     25.4                75.0        70.0         0.0       -5.0
Te2/1/4     25.4                75.0        70.0         0.0       -5.0

                              High Alarm  High Warn  Low Warn   Low Alarm
           Voltage            Threshold   Threshold  Threshold  Threshold
Port       (Volts)            (Volts)     (Volts)    (Volts)    (Volts)
---------  ---------------    ----------  ---------  ---------  ---------
Te1/1/4    3.31                  3.63        3.46        3.13       2.97
Te2/1/4    3.31                  3.63        3.46        3.13       2.97

           Optical            High Alarm  High Warn  Low Warn   Low Alarm
           Transmit Power     Threshold   Threshold  Threshold  Threshold
Port       (dBm)              (dBm)       (dBm)      (dBm)      (dBm)
---------  -----------------  ----------  ---------  ---------  ---------
Te1/1/4     -1.7                 3.4         0.4        -8.1      -12.1
Te2/1/4     -1.9                 3.4         0.4        -8.1      -12.1

           Optical            High Alarm  High Warn  Low Warn   Low Alarm
           Receive Power      Threshold   Threshold  Threshold  Threshold
Port       (dBm)              (dBm)       (dBm)      (dBm)      (dBm)
-------    -----------------  ----------  ---------  ---------  ---------
Te1/1/4     -6.9                 3.4         0.4       -14.4      -18.3
Te2/1/4     -8.2                 3.4         0.4       -14.4      -18.3

        
Copy interface name which you want to monitor (for example Te1/1/4 and Te2/1/4)

in PRTG:
1. Copy file transeiverstatusssh.exe to \PRTG Network Monitor\Custom Sensors\EXEXML folder
2. Copy file SFPdata.ovl to \PRTG Network Monitor\lookups\custom folder
3. Go to PRTG->Setup->System Administration->Administrative Tools for the Core Server and click Load Lookups
4. In devices settings add credentials for Linux/Solaris/Mac OS (Your user for SSH)
5. Add EXE/Script Advanced sensor, in dropdown list, select transeiverstatusssh.exe
6.Parameners must be: -h %host -u %linuxuser -pw %linuxpassword -i Interface names separated by comas
Example: -h %host -u %linuxuser -pw %linuxpassword -i Te1/1/4,Te2/1/4