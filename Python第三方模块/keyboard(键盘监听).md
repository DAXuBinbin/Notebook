# Keyboard - 键盘监听模块

## 一、安装

> pip install keyboard

## 二、使用

```python
# 字符
# '1'
# 'a'
# ...
# 控制
# 'ctrl'
# 'alt'
# 'shift'
# 'enter'
# 'esc'
# 'f1'
# ...
# 方向键
# 'up'
# 'down'
# 'left'
# 'right'
#组合按键
# 'ctrl'+'alt'+'a'
# ...
```

#### 常用方法

##### wait()

监听按键，如果没设置按键，将会一直监听这句之前的按键；如果设置了按键，那么在按下该按键后就会停止监听，并执行后面的语句

```python
import keyboard

print(0)
keyboard.wait('a')
#在按下a之前后面的语句都不会执行，下面同理
print(1)
keyboard.wait('b')
print(2)
keyboard.wait('c')
print(3)
keyboard.wait()

结果：
0
1
2
3
#继续监听
#只有按顺序按下abc（中间过程随便按不干扰）才能输出0123，但因为最后一个没设置按键，所以会一直监听下去
```

