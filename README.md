# iterm2-zmodem

Zmodem for iTerm2

## Install

1. Install lrzsz.(安装lrzsz使支持zmodem)

```sh
brew install lrzsz
```

2. Save ```iterm2-zmodem.sh``` to your PATH（保存脚本并给执行权限。链接位置我就不改了是fork过来的地址）

```sh
wget -qO /usr/local/bin/iterm2-zmodem https://github.com/kuoruan/iterm2-zmodem/raw/master/iterm2-zmodem.sh
chmod +x /usr/local/bin/iterm2-zmodem
```

3. Add triggers in iTerm 2 'Preferences...' -> 'Profiles' -> 'Advanced' -> 'Trigger', click 'Edit'（创建触发器）

```
Regular expression: rz waiting to receive.\*\*B0100
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-zmodem send
Instant: checked

Regular expression: \*\*B00000000000000
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-zmodem recv
Instant: checked
```

<img width="885" alt="image" src="https://user-images.githubusercontent.com/49583211/191404198-6dd69b51-1896-4c11-b6aa-c0d00b466adc.png">


but  如果你不是直接链接的服务器，会破坏掉zmodem。中间有跳板机就会失败
例如A-B access
A-B-C a取c文件 fail
解决方式就是直接登录B的时候登录C
