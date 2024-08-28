# Hadoop 的安装和使用

>[!NOTE] 内容
> 

不想配虚拟机了～～直接腾讯云搞一台

1. 4C8G 足够

![image-20240828155356777](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281553920.png)

2. 直接 Ubuntu 22.04 LTS 吧

![image-20240828155413782](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281554895.png)

3. 网络

![image-20240828155523588](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281555678.png)

![image-20240828155537423](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281555514.png)

直接用 ssh 连接吧

![image-20240828155658201](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281556305.png)

![image-20240828160330421](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281603510.png)

```sh
sudo apt update
sudo apt upgrade
```

![image-20240828160350844](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281603938.png)

![image-20240829001638369](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290016481.png)

![image-20240829001712611](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290017723.png)

![image-20240829001811160](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290018257.png)

直接 OK 更新完成

![image-20240829001930320](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290019424.png)

先将需要的软件传上去

![image-20240828160502939](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281605013.png)

![image-20240829000601314](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408281606721.png)

> [!CAUTION]
>
> 此处就不操作 ssh 了，反正用完就删了

等待上传期间操作创建下目录结构吧

![image-20240829001444642](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290014702.png)

```sh
mkdir dev && cd dev
mkdir java
mkdir hadoop
```

正好上传完了

![image-20240829001529056](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290015159.png)

直接配置 Java 

```sh
sudo tar -zxvf ./jdk-8u162-linux-x64.tar.gz -C ./dev/java
```

![image-20240829002034246](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290020346.png)

将 Java 添加到环境变量

```sh
vim ~/.bashrc
```

```sh
# JAVA PATH
export JAVA_HOME=/home/ubuntu/dev/java/jdk1.8.0_162
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH
```

![image-20240829002205050](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290022159.png)

```sh
source ~/.bashrc
```

验证

```sh
java -version
```

![image-20240829002225506](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290022573.png)

安装 hadoop

````sh
sudo tar -zxf ./hadoop-3.1.3.tar.gz -C ./dev/hadoop

cd dev/hadoop
````

移动文件到当前目录

```sh
mv hadoop-3.1.3/* .
```

配置权限 （直接 777 吧）

```sh
cd ..
sudo chmod 777 ./hadoop/
```

将 Hadoop 加入到 PATH

```sh
vim ~/.bashrc
```

```sh
# HADOOP PATH
export HADOOP_HOME=/home/ubuntu/dev/hadoop
export PATH=${HADOOP_HOME}/bin:${HADOOP_HOME}/sbin:$PATH
```

![image-20240829004703643](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290047754.png)

```sh
source ~/.bashrc
```

验证

```sh
hadoop version
```

![image-20240829004802062](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290048147.png)

先玩玩单机模式，使用 hadoop 自带的 jar 统计单词出现次数

```java
mkdir input
cp ./etc/hadoop/*.xml ./input
ls input/
hadoop jar ./share/hadoop/mapreduce/hadoop-mapreduce-examples-3.1.3.jar grep ./input ./output 'dfs[a-z.]+'
```

![image-20240829005406873](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290054000.png)

执行完成

![image-20240829005450814](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290054918.png)

查看执行结果

```sh
cat ./output/*
```

![image-20240829005441524](https://mcdd-dev-1311841992.cos.ap-beijing.myqcloud.com/assets/202408290054600.png)

可以看到输出结果符合正则表达式的单词 dfsadmin 出现了 1 次，接下来再玩玩伪分布式 我们需要修改其配置文件



# 一、

>[!NOTE] 内容
> 

## 1.1

## 1.2

## 1.3

## 1.4

# 二、

>[!NOTE] 内容
> 

## 2.1

## 2.2

## 2.3

## 2.4


# 三、

>[!NOTE] 内容
> 

## 3.1

## 3.2

## 3.3

## 3.4

# 四、

>[!NOTE] 内容
> 

## 4.1

## 4.2

## 4.3

## 4.4

# 五、

>[!NOTE] 内容
> 

## 5.1

## 5.2

## 5.3

## 5.4

# 六、

>[!NOTE] 内容
> 

## 6.1

## 6.2

## 6.3

## 6.4