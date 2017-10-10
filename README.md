# SYSU H3C Client

A CLI H3C Client for Padavan

代码大部分参考了https://github.com/zonyitoo/sysuh3c

修改了部分代码以适配Padavan, 提供了编译好了的sysuh3c （应该只能在k2等MT7620芯片的路由器上运行)

*Only tested in SYSU east campus*

## Compilation

### Compile with Padavan-SDK

首先先参考[教程](http://blog.csdn.net/maxsky/article/details/53905221)

做到交叉编译工具链那一步就可以了

记得把交叉编译工具链放在/opt目录下

接着修改~/.bashrc，加上下面东西

export padavan_bin=/opt/padavan/rt-n56u/toolchain-mipsel/toolchain-3.4.x/bin #（此处要按自己的交叉编译工具链位置来修改）

export PATH=$PATH:/opt/padavan/rt-n56u/toolchain-mipsel/toolchain-3.4.x/bin

export AR=$padavan_bin/mipsel-linux-uclibc-ar

export AS=$padavan_bin/mipsel-linux-uclibc-as

export LD=$padavan_bin/mipsel-linux-uclibc-ld

export NM=$padavan_bin/mipsel-linux-uclibc-nm

export CC=mipsel-linux-uclibc-gcc

export CPP=mipsel-linux-uclibc-cpp

export GCC=mipsel-linux-uclibc-gcc

export CXX=mipsel-linux-uclibc-g++

export RANLIB=mipsel-linux-uclibc-ranlib

export ac_cv_linux_vers=2.6.32

export LDFLAGS="-static"

export CFLAGS="-Os -s


接着执行source ~/.bashrc 

然后在src 目录下执行make，就会编译出sysuh3c这个文件，放到路由器上面运行就可以了

上面添加的东西也可以删除

## Usage

```bash
-h --help        print help screen
-u --user        user account
-p --password    password
-i --iface       network interface (default is eth0)
-m --method      EAP-MD5 CHAP method [xor/md5] (default xor)
-d --daemonize   daemonize
-c --colorize    colorize
-l --logoff      logoff
```
## Thanks

[sysuh3c](https://github.com/zonyitoo/sysuh3c)
