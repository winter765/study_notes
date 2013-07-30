Linux（ubuntu）虚拟内存的设置(转自www.2cto.com作者 被射下的眼泪)
 
swap空间就是虚拟内存，在物理内存不足时，有较大的用处。
 
查看内存空间大小：free -m // m表示显示的字节单位是m（megabytes）
 
下面我们就来增加系统的 Swap 大小。  www.2cto.com  
 
1.首先用命令free查看系统内 Swap 分区大小。
free -m
 
total used free shared buffers cached
Mem: 1002 964 38 0 21 410
-/+ buffers/cache: 532 470
Swap: 951 32 929
 
可以看到 Swap 只有951M，不符合 Oracle-xe-client 的安装要求。
 
2.创建一个 Swap 文件。
mkdir swap
cd swap  www.2cto.com  
sudo dd if=/dev/zero of=swapfile bs=1024 count=100000
 
出现下列提示，上面命令中的 count 即代表swap文件大小。
 
记录了 100000+0 的读入
记录了 100000+0 的写出
102400000 字节 (102 MB) 已复制，0.74704 秒，137 MB/秒
 
把生成的文件转换成 Swap 文件
sudo mkswap swapfile
 
Setting up swapspace version 1, size = 102395 kB
no label, UUID=09fde987-5567-498a-a60b-477e302a988b
 
3.激活 Swap 文件。
sudo swapon swapfile
 
再次查看 free -m 的结果。
 
total used free shared buffers cached
Mem: 1002 967 34 0 22 410
-/+ buffers/cache: 534 467
Swap: 1053 32 1021  www.2cto.com  
 
添加成功。
 
扩展：
如果需要卸载这个 swap 文件，可以进入建立的 swap 文件目录。执行下列命令。
sudo swapoff swapfile
 
如果需要一直保持这个 swap ，可以sudo -s换到root
然后把它写入 /etc/fstab 文件。
 
swapfilepath swap swap defaults 0 0
