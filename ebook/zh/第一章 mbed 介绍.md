# 1 mbed介绍 #
## 1.1 什么是mbed ##
**mbed是什么?**

  mbed是一个面向ARM处理器的原型开发平台，它具体包括免费的软件库（SDK），硬件参考设计（HDK）和在线工具（Web）三部分内容，各个部分的具体介绍如下：

  SDK：mbed设计了一个硬件抽象层，从而屏蔽了不同mcu厂商提供了微处理之间的差异，对于用户来说，他只需要和这个硬件抽象层打交道即可，也就是说，用户基于mbed开发的应用可以很方便地更换使用不同厂商的arm微处理器，从而留给用户更多的选择。

  HDK：HDK是mbed提供的硬件参考设计，它是面向用户开发设计的，所以HDK提供了统一了程序上载接口，单步调试接口，串口调试接口，用户无需购买其它硬件就可以开始软件开发工作。

  WEB：为了省去用户开发环境安装的麻烦，mbed提供了一个完备的基于浏览器的微处理器软件开发环境，包括代码编写，程序编译，版本控制等功能，用户只要上网就可以开发，编译结果只要下载保存到mbed开发板上即可工作，非常方便。

mbed的体系结构
  mBed是ARM公司官方提供的一套用于快速开发ARM架构单片机应用原型的工具集，包括免费的软件库（Software Development Kit,SDK），硬件设计参考（Hardware Development Kit,HDK）和基于Web的在线编译环境（mBed Compiler）三部分具体内容。所以，在不同的上下文中，mBed有可能指的是mBed SDK，也有可能指的是mBed开发板。由于mBed的代码和大部分硬件设计都是以开源（Open Source，permissive Apache 2.0 licence）的方式提供的，再加上它面向的ARM系列单片机具有较高的性价比和广泛的应用基础，所以mBed在世界范围内已经吸引了大量的电子产品开发者，其产业生态链已经初级规模。
   
mBed SDK
  mBed SDK是一个面向C/C++的单片机软件开发框架，它建立在大量牛人开发的代码之上，可以让我们快速地开发各种基于ARM的单片机应用项目。mBed SDK已经帮我们完成了启动代码的编写，相关运行库的封装和单片机外设的抽象，从而使我们抽出更多的时间来关注具体的项目应用。而且，更为关键的是，mBed SDK采用开源的permissive Apache 2.0 licence，从而使我们既可以把它应用于个人学习，也可以应用于商业研发，为日后的产品销售做好准备。

  下面是一个基于mBed SDK开发的LED（发光二极管）闪烁程序，同样的功能，如果我们从头开始编写那可能需要上百行代码，而这里只需要10行，而且代码清晰易懂，更接近人的思维方式，这足以显示mBed SDK的强大：

```c
#include "mbed.h"
 DigitalOut myled(LED1);
 int main() {
    while(1) {
        myled = 1;
        wait(0.2);
        myled = 0;
        wait(0.2);
    }
}
```

  mBed SDK当前已经支持大量的单片机，包括NXP公司的LPC11UXX、LPC11XX、LPC11CXX、LPC13XX、LPC23XX、LPC43XX、LPC81X、LPC176X、LPC408X系列，ST公司的STM32F030R8、STM32F103R8、STM32F401RE、STM32L152RE、STM32F4XX系列，FREESCALE公司的MK20D5M、MKL05Z、MKL25Z、MKL46Z系列，NORDIC公司的NRF51822，而且还在不断增加中，当然，即使mBed SDK不支持的单片机，用户也可以自行移植使用，所以mBed SDK具有很大的应用范围。
虽然mBed官方推荐使用它提供的在线开发工具进行开发，这虽然省去了用户安装开发环境需要的时间，但由于所有的代码都需要放在云端，而且只有联网的计算机才能使用，所以国人并不习惯，这也是mBed迟迟没有在国内流行起来的重要原因，好在国内的SMeshLink公司已经开发出了基于Eclipse和Gcc的离线IDE环境，从而为mBed的国内流行扫清了障碍，当然，如果你要使用的MCU 不支持GCC编译mBed SDK，那就需要自行添加启动文件和链接文件后才能使用，该环境当前主要支持GCC ARM Embedded编译器。

mBed HDK

  为了方便用户的快速开发，mBed提供了HDK接口设计参考，其核心是通过一个实现统一协议的接口单片机来实现用户的程序上载，代码调试和串口监控，其硬件设计和固件代码都是公开的，但当前只支持有限的几个mcu，包括LPC812M10、LPC1768和LPC11U24，再加上增加接口MCU后硬件的成本会增加，所以用户并没有需要使用该方案来上载程序，我们使用的是串口上载方式，只要有串口就能上载，当然，这样就没有调试功能了。

mBed Compiler

  为了用户开发的方便，mBed官方提供了网页版的开发工具，用户只要有联网的计算机就可以开始基于mBed的开发，在加上mBed的上载方式就是复制，是所有操作系统都支持的操作，所以，理论上来说，用户可以在所有的操作系统上进行开发，包括windows，IOS,Anrdoid及Linux等。mBed Compiler的主要功能如下：

硬件开发的新时代，为什么是mbed

  mbed是一个以ARM控制器为基础的软件开发平台，旨在统一基于ARM控制器软件开发平台。ARM控制器软件开发平台 第一阶段，面向控制器的寄存器操作；第二阶段ARM公司推出Cortex M处理器时，各半导体推出对寄存器操作函数库；第三阶段应该就是mbed所开启的新的。

以下文章“mbed比Arduino好吗”
  引自[http://mbed.smeshlink.com/faq/5-mbed-arduino](http://mbed.smeshlink.com/faq/5-mbed-arduino)这不是一个简单能够回答的问题，任何事物都有自己的应有范围，所以我们不能简单地说mbed比Arduino好，或者Arduino比mbed好，它们都有自己的生命周期和应用领域，我既在Arduino上作过深入开发，也对mbed做了细致的了解，对于我的感触是，mbed的开发更加简单，更加方便。在很多应用领域有很好的应用，读者可以自己体会。
## 1.2 mbed有哪些优点 ##

## 1.3 mbed SDK体系结构 ##

  为了更好地利用mbed sdk进行开发，我们有必要了解一下mbed sdk的设计理念及目录结构。mbed sdk的最大价值在于提供一个面向微处理器硬件的抽象层，从而使用户在开发具体应用时无需了解具体的硬件结构，从这点上来看，用户开发mbed应用程序和开发windows应用程序并无太大的不同，其具体结构如下：

![mbed 体系结构.png](http://upload-images.jianshu.io/upload_images/55705-78a4bd161c31acd5.png)

  具体来说，mbed/api目录中存放的是用户需要调用的mbed相关的.h头文件，mbed/commpn目录中存放的是这些.h文件的具体实现，它会调用mbed/hal中的.h文件，而mbed/targets/hal中存放的则是mbed/hal中这些.h文件的具体实现，不同的mcu需要不同的实现，同一mcu不同应用板也需要不同的实现，而mbed/targets/cmsis中存放的则是mcu与外设之间的接口及启动链接文件，其中的代码不但与mcu相关，还有具体的编译器相关，所以同一个mcu下还有多个目录。

## 1.4 怎么参与mbed项目开发 ##

  通过详细学习后面章节的教程，您很快就了解了mbed的开发流程以及特点，为您进行mbed项目开发打下良好的基础。对本教程的内容熟悉后，相信对读者您参与项目开发有很大的帮助。
