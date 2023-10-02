# Scubajet SSC Arduino Library

Arduino library for interfacing with a SCUBAJET Portable over UART.


## Usage

Initialize VescUart class and select Serial port for UART communication.  
  
```cpp
#include <ScubaUart.h>

VescUart UART;

void setup() {
  Serial.begin(9600);

  UART.setSerialPort(&Serial);
}
```

Avalibe functions:
  
```cpp         
void setSCUBA_POWER_ON();          //Must be called in the fist 200ms after Power on

void sendSCUBA_POWER_KEEPALIVE();  //Activates SSC Powwer for 135sec 

void setSCUBA_LED_ON();  //Turn on NOSE-LED  

void setSCUBA_LED_OFF(); //Turn off NOSE-LED

void sendKeepalive(); //Musst be send every 1s 

/**
* @brief      Sends a command to the Motor to spin
* @param      Motor-Current in [mA] (Full Power are 45000mA)
*/
void setCurrent([current in mA]); //Spin Motor with specific Current

/**
* @brief      Sends a command to VESC and stores the returned data
* @return     True if successfull otherwise false
*/
bool getVescValues(void);
```

Telemetry: 

```cpp 
//For example: 
float batt_voltage = UART.data.v_in;

//Parameters:
float v_in;
float temp_fet;
float temp_motor;
float temp_mos3;
float temp_mos4;
float temp_mos5;
float temp_mos6;
float temp_pcb;
float current_motor;
float current_in;
float rpm;
float duty_now;
float amp_hours;
float amp_hours_charged;
float watt_hours;
float watt_hours_charged;
int32_t tachometer;
int tachometer_abs;
float avgMotorCurrent;
float avgInputCurrent;
float dutyCycleNow;
float ampHours;
float ampHoursCharged;
float wattHours;
float wattHoursCharged;
float pidPos;
uint8_t id;
int error; 
int fault_code;
```
