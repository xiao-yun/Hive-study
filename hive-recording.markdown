#安装
##版本
	>hive-1.1.0
###配置
	>hive.metastore.warehouse.dir,hive在HDFS中数据存储位置;
	>hive.exec.local.scratchdir,本地目录；
	>hive.hwi.war.file,hwi war文件位置;
###问题
	>hive-site.xml有时能解析环境变量(如${HIVE_HOME})，有时不行，不知道为什么;
###关于HWI
	1.下载的hive-1.1.0.bin.tar.gz没有hive-hwi-*.war包，需下载源码，将hwi目录下web子目录
	通过jar打包,在源码hwi目录下:
	`jar xcfM0 $HIVE_HOME/lib/hive-hwi-1.1.0.war -C web/ .`
	打包后，放入lib目录下；
	2.注意，hive和hwi不能同时运行，即运行hive后，通过hive --service hwi运行hwi服务，在web界面
	执行相关操作会出现异常；而且hwi只能通过Ctrl+C来终止，web界面也没什么服务，很不好用；
###关于hive-1.1.0源码的编译安装
	*目前通过mvn clean install -Phadoop-1,dist无法完成编译安装；
	*其中指定hadoop-1，在设置环境变量$HADOOP_HOME情况下，对应hadoop版本为$HADOOP_HOME指定的版本，
	本记录前为hadoop-1.2.1。总是在hive-common编译不过，提示各种找不到符号，classpath设置了hadoop/lib目录的；
