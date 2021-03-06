# Art和Dalvik区别


##### 区别
Android 4.4发布了一个ART运行时，准备用来替换掉之前一直使用的Dalvik虚拟机

Art: Android Runtime，编译机制：AOT，预编译机制
Dalvik：编译机制：JIT，即时编译

ART 的机制与 Dalvik 不同。在Dalvik下，应用每次运行的时候，字节码都需要通过即时编译器（JIT，Just-In-Time）转换为机器码，这会拖慢应用的运行效率，而在ART 环境中，`应用在安装的时候，字节码就会预先编译成机器码`，使其成为真正的本地应用。这个过程叫做预编译（AOT,Ahead-Of-Time）。这样的话，应用的启动(首次)和执行都会变得更加快速。


##### 什么是Dalvik

Dalvik是Google公司自己设计用于Android平台的Java虚拟机。Dalvik虚拟机是Google等厂商合作开发的Android移动设备平台的核心组成部分之一，它可以支持已转换为.dex(即Dalvik Executable)格式的Java应用程序的运行，.dex格式是专为Dalvik应用设计的一种压缩格式，适合内存和处理器速度有限的系统。Dalvik经过优化，允许在有限的内存中同时运行多个虚拟机的实例，并且每一个Dalvik应用作为独立的Linux进程执行。独立的进程可以防止在虚拟机崩溃的时候所有程序都被关闭。

##### 什么是ART

Android操作系统已经成熟，Google的Android团队开始将注意力转向一些底层组件，其中之一是负责应用程序运行的Dalvik运行时。Google开发者已经花了两年时间开发更快执行效率更高更省电的替代ART运行时。ART代表Android Runtime,其处理应用程序执行的方式完全不同于Dalvik，Dalvik是依靠一个Just-In-Time(JIT)编译器去解释字节码。开发者编译后的应用代码需要通过一个解释器在用户的设备上运行，这一机制并不高效，但让应用能更容易在不同硬件和架构上运行。ART则完全改变了这套做法，在应用安装的时候就预编译字节码到机器语言，这一机制叫Ahead-Of-Time(AOT)编译。在移除解释代码这一过程后，应用程序执行将更有效率，启动更快。


ART优点：

* 系统性能的显著提升
* 应用启动更快、运行更快、体验更流畅、触感反馈更及时
* 更长的电池续航能力
* 支持更低的硬件

ART缺点：

* 更大的存储空间占用，可能会增加10%-20%
* 更长的应用安装时间
