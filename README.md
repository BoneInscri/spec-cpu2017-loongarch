

0. **获取iso文件并安装**

<a href="https://pan.baidu.com/s/1kMoMJ5Ufg5oZql4HjyacAg" rel="nofollow">镜像文件下载</a>

提取码：5thr

```
sudo mount cpu2017-1.0.5.iso /mnt
cd /mnt
./install.sh
```

注意安装路径



1. **设置bin的环境变量**

```
sh shrc
```



2. **update**

```
runcpu --update
```



3. **交叉编译的config文件**

```
loongarch64.cfg
```

需要放入config/中



4. **编译命令**

```
runcpu --config=loongarch64 --action=build all
```



5. **修改原文件，消除部分子测试的error&warn**

```
./benchspec/CPU/525.x264_r/src/ldecod_src/configfile.c
增加InputParameters cfgparams;
```

```
./benchspec/CPU/525.x264_r/src/ldecod_src/configfile.h
InputParameters cfgparams; 修改为
extern InputParameters cfgparams;
```



6. **测试指令**

```
# 运行单个测试（例如 500.perlbench_r）
runcpu --config=loongarch64.cfg --action=run 500.perlbench_r

# 运行全部测试
runcpu --config=loongarch64.cfg --action=run all
```
