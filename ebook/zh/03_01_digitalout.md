# DigitalOut #
## API函数详细介绍 ##
该DigitalOut接口用于配置和控制数字输出引脚。DigitalOut类有以下几个方法；所有函数采用C++类的封装思想。函数为公有属性。主要函数有read()、write()等。
```{c}
/*DigitalInOut example.*/
 
#include "mbed.h"
 
DigitalInOut pin(PC_6);
DigitalIn key1(USER_BUTTON1);
 
int main() {
    unsigned int value =0;
    pin.output();
    pin = 0;    
    wait_us(500);
    while(1)
    {
      value=key1.read();
        if(value)
        {
            pin.output();
            pin = 1;
            wait_us(500);
        }
        else
        {
            pin = 0;
            wait_us(500);
        }
    }
}

```
