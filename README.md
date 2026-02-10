# Snake Dongle Module 🐍

Snake Dongle is a compact, highly customizable ZMK-powered dongle that features a Snake‑game-style animation and optional sound effects.
Complete documentation [here](https://github.com/joaopedropio/snake-dongle).
Click [here](https://www.youtube.com/watch?v=xdSUZYLVVY0) to watch a demo.

<img src="https://i.imgur.com/5ogG2z9.jpeg"/> 

## Backlight
### On the dongle repo
Check [nice_nano.overlay](https://github.com/felixJR123/module-snake-dongle/blob/backlight/boards/shields/snake_adapter/boards/nice_nano.overlay) and [snake_adapter.overlay](https://github.com/felixJR123/module-snake-dongle/blob/backlight/boards/shields/snake_adapter/snake_adapter.overlay)  
I commented all the changes I made so should be easy to follow.

### On the keyboard repo
+ In the dongle.overlay add  
```
/ {  
	chosen {  
       zmk,backlight = &lcd_backlight;  
    };  
};
```

+ In the dongle.conf add
```
# Enable Backlight Control
CONFIG_ZMK_BACKLIGHT=y
CONFIG_ZMK_BACKLIGHT_BRT_START=100
CONFIG_ZMK_BACKLIGHT_ON_START=y
CONFIG_ZMK_BACKLIGHT_AUTO_OFF_IDLE=y
```

+ In Kconfig.defconfig on the set up for the dongle shield add
```
if ZMK_BACKLIGHT

config PWM
    default y

config LED_PWM
    default y

endif # ZMK_BACKLIGHT
```