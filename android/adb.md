## adb {#adb}

1 、安装 应用到模拟器：

adb install

比较遗憾的是，Android并没有提供一个卸载 应用的命令，只能自己手动删除 ：

adb shell

cd /data/app

rm app.apk

2、进入设备或模拟器的shell：

adb shell

通过上面的命令，就可以进入设备或模拟器的shell环境中，在这个Linux Shell中，你可以执行各种Linux 的命令，另外如果只想执行一条shell命令，可以采用以下的方式：

adb shell [command]

如：adb shell dmesg会打印出内核的调试信息。

3、发布端口：

可以设置任意的端口号，做为主机 向模拟器或设备的请求端口。如：

adb forward tcp:5555 tcp:8000

4、复制文件 ：

可向一个设备或从一个设备中复制文件，

复制一个文件或目录到设备或模拟器上：

adb push

如：adb push test.txt /tmp/test.txt

从设备或模拟器上复制一个文件或目录：

adb pull

如：adb pull /addroid/lib/libwebcore.so .

5、搜索模拟器/设备的实例：

取得当前运行的模拟器/设备的实例的列表及每个实例的状态：

adb devices

6、查看bug报告：

adb bugreport

7、记录无线通讯日志：

一般来说，无线通讯的日志非常多，在运行时没必要去记录，但我们还是可以通过命令，设置记录：

adb shell

logcat -b radio

8、获取设备的ID和序列号：

adb get-product

adb get-serialno

9、访问数据库SQLite3

adb shell

sqlite3