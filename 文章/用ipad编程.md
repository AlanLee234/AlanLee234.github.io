### 用ipad编程

#### 一、

开始的策略是通过ipad上传至NextCloud，进行同步，通过Shell进行编译。

为了简便开发，学习使用了Shell，进行自动化编译运行。

Shell

https://www.runoob.com/linux/linux-shell.html

Shell_Linux Shell 中实现字符串切割的几种方法

https://blog.csdn.net/u010003835/article/details/80750003

```shell
#！/bin/sh
echo "Run sh!"

#有参数时，执行；无参数跳转

if [ $# == 1 ]
then
	FileName=$1
        array=(${FileName//./ }) 

    if [[ ${array[1]} = "cpp" ]]
    then
	echo "Program cpp:"
            cd /var/www/html/nextcloud/data/admin/files/ccf/cpp
	g++ $1 -o ${array[0]}
	echo -e "--------Run cpp--------"
        ./${array[0]}
        cd /root  	
	echo "--------Over!--------"
    elif [[ ${array[1]} = "java" ]]
    then
            echo "Program java:"
	cd /var/www/html/nextcloud/data/admin/files/ccf/java
	javac $1
	echo -e "--------Run java--------"
	java ${array[0]}
	echo "--------Over!--------"
	cd /root
    else
            echo "other"
    fi

else
        cd /var/www/html/nextcloud/data/admin/files/ccf
	echo "Now at:"
	pwd
fi
```

**问题：**

在网页端不能显示直接在文件系统里添加上的文件，只能显示通过客户端上传的文件。

之后想更改设置，让nextcloud自动扫描更心文件，设置时发现无权限。（https://docs.nextcloud.com/server/20/admin_manual/configuration_files/external_storage_configuration_gui.html#enabling-external-storage-support）发现是因为缺php控件posix（https://docs.nextcloud.com/server/20/admin_manual/installation/source_installation.html#prerequisites-for-manual-installation）

同时无法定位php和MariaDB的安装位置，这个以后安MySql时要注意，可能会存在版本冲突。

#### 二、

发现Testastic可以连接命令行，并直接将文件上传至服务器，遂觉得采用此方法。

