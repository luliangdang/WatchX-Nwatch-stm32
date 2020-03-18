移植到Stm32的NWatch

![Nwatch](data:image/jpg;base64,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)




首先感谢zkemble在2015年提供的 [NWatch](https://github.com/zkemble/NWatch) ，真的是太棒了

其次是 [crystaledm](https://github.com/crystaledm/watchX) 提供的c语言库，谢谢


### 开发环境： 

keil5  ALIENTEK 探索者STM32F407开发板  2.4寸tft屏幕

### 目前已经完成的移植内容为：

RTC时钟、动画显示、断电flash模拟eeprom，及其自带的所有图标

### 待完成：             

闹铃的flash存储，Sleep睡眠模式（低功耗模式），电压检测，音调，音量调节

### 可实现的效果：

闹钟、手电筒、秒表计时、3D动画演示、游戏（赛车、破坏小球）
             设置->日期调整、（睡眠时间设置）、显示设置、版本信息查看、FPS显示

### 感兴趣的小伙伴可以进群：

我还没创，你自己建吧！		
                                                  

### 主要的菜单界面可以阅读借鉴：

setting.c 的迭代器函数  

```
static void itemLoader(byte num)   
```

同时注意

```
 #define OPTION_COUNT	5
```

中间的OPTION_COUNT 根据实际情况进行增加减少 

```
  void setMenuOption_P(byte num, const char* name, const b yte* icon, menu_f actionFunc) 
```

 中的actionFunc  根据Go to Definition  of "xxxxx" 就可以进入对应的文件进行修改，也可以模仿进行添加文件

还有一种菜单模式，可以借鉴 timedate.c 和 diag.c



在Typedefs.h里面的这几个函数指针需要留意

```
typedef display_t (*draw_f)(void);
typedef void (*display_f)(void);
typedef bool (*button_f)(void);
typedef void (*menu_f)(void);
typedef void (*itemLoader_f)(byte);
```

不太懂函数指针的可以查看[typedef void (*Fun) (void)]( https://blog.csdn.net/u014221279/article/details/50978204 )

[结构体内的函数指针]( https://www.cnblogs.com/lvjunjie/p/8961731.html )

### 屏幕移植到oled ：

对于想将屏幕移植到oled 的小伙伴，只需要将void oled_flush(void)重写，将oledBuffer[]数组输出到oled屏幕上，将因为手上还没有oled 我在TFT屏幕上模拟了oled 的显示方式，无需修改其他位置

### 移植到其它stm32单片机：

对于想移植到其它stm32单片机上的小伙伴，需要特别注意appconfig.c中间的eepCheck_SAVE_ADDR 这个偏移地址，请适当调整
 EEPROM_CHECK_NUM这个值很玄学，我尝试了很久才出来

移植和改动文件程序的时候需要主要：  common.h
对部分预编译效果不满意的可以修改：       config.h

### 其它：

横屏显示的骚操作在 lcd.c LCD_Fast_DrawPoint 里面随便乘以了一个倍数

对了这个lcd.c是我简化过正点原子的库的，对你自己的屏幕需要你找个可以用的屏幕库修改一哈

## 希望大家疫情期间玩的开心，保重身体！！！

​      