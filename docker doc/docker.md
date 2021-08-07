## **一：容器命令**

#### 	**A.删除容器**

​	docker rm -f $(docker ps -aq)

#### 	**B.查看容器**

​	docker ps

#### **C.运行容器**

​	docker run -it 镜像名 /bin/bash

#### **D.停止容器**

​	docker stop 容器ID

#### **E.启动容器**

​	docker start 容器ID

## **二：镜像命令**

#### **A.搜索镜像**

​	docker search 镜像名

#### **B.下载镜像**

​	docker pull 镜像名称

#### **c.查看镜像**

​	docker  images 

#### **D.删除镜像**

​	docker rmi -f 镜像ID

#### **E.下载镜像**

​	docker pull elasticsearch:7.6.2

#### **F：提交镜像**

​	docker commit -a="jack" -m="add tomcat" 容器ID tomcat02:1.0

#### **G:查看镜像构建过程**

​	docker history 镜像ID

## ***三：其他常用命令****

#### 	**A.启动镜像**

​	docker run -d   镜像名   #  $\textcolor{RedOrange}{后台运行，没有交互模式}$

​	docker run -it centos /bin/bash #$\textcolor{RedOrange}{交互模式运行，按ctrl+p+q退出}$

#### 	B.查看日志

​	docker logs -ft --tail 10 镜像名\ID

#### 	**c.查看容器中进程信息**

​	docker top 镜像名\ID

#### 	**d.查看镜像的元数据**

​	docker inspect 镜像名\ID

#### 	**e.进入当前正在运行的容器**

​	docker exec -it 镜像名\ID /bin/bash     #  $\textcolor{RedOrange}{输入exit可以退出容器}$

​	 docker attach  镜像名\ID                  #  $\textcolor{RedOrange}{进入正在运行的容器}$

#### 	**f.从容器内拷贝文件到主机上**

​	docker cp -a 容器ID:/home/test.java /root

#### **g.查看容器转态**

​	 docker stats

## 四：容器数据卷**

​	docker run -it -v /home/testv:/home centos /bin/bash  #/home/testv为本地目录   /home为 容器内目录 

​	docker run -it --name centos02 --volumes-from centos01 21b4b8a1da1e   #容器之间的数据卷同步

## **五：具名挂载和匿名挂载**

​	docker run -d --name nginx01 -P -v /etc/nginx nginx #匿名挂载      -P随机端口   /etc/nginx容器内路径 



​	docker volume ls    #查看挂载对应 的卷名 

​	docker run -d --name nginx02 -P -v juming:/etc/nginx nginx   #juming:/etc/nginx 卷名：容器内路径

## **六：dockerfile构建镜像的构建文件**

​	a.vi dockerfile1                                                                      #创建dockerfile1文件

​    b.FROM centos                                                                      #dockerfile脚本

​		VOLUME ["volume01","volume02"]

​		CMD echo "successful"

​		CMD /bin/bash

​	c.docker build -f dockerfile1 -t jackdocker/centos:1.0 .  #构建镜像文件

## **七：dockerfile常用命令**

​	FROM                         #基础镜像

​	MAINTAINER             #镜像作者，姓名+邮箱

 	RUN                          #镜像构建的时候需要运行的命令 

​	ADD                           #添加内容

​	WORKDIR                  #镜像工作目录

​	VOLUME                    #挂载的目录

​	EXPOST                      #暴露端口

​	CMD                           #指定这个容器启动的时候要运行的命令

​	ONBUILD                   #当构建一个被继承DOCKERFILE 这个时候就会运行ONBUILD的指令 

​	COPY                          #类似ADD,将文件拷贝到镜像中

​	ENV                            #构建的时候设置环境变量

## 八：实例安装**

## **A：nginx安装**

​	docker run -d --name ngixtest -p 3344:80 nginx

## **B：安装tomcat**

​	docker run -d  -p 3355:8080 tomcat

## **C：安装elasticsearch**

​	docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.6.2

​	docker run -d -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e ES_JAVA_OPTS="-Xms64m -Xmx521m" elasticsearch:7.6.2  #限制运行内存

​	curl localhost:9200       #测试命令

#### **D.安装portainer（可视化）运用**

​	docker run -d -p 8088:9000 --restart=always -v /var/run/docker.sock:/var/run/docker.sock --privileged=true portainer/portainer

测试：浏览器输入IP+端口号

## **E:安装MYSQL**

​	docker run -d -p 3310:3306 -v /home/mysql/conf:/etc/mysql/conf.d -v /home/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=@c12580 mysql

#### **F:构建自己的centos镜像**

1：编写dockerfile文件

![](../pitures/%E6%8D%95%E8%8E%B7.PNG)

   2：通过dockerfile文件来构建镜像

​		docker build -f mycentos -t jackcentos:1.1 . 

3：运行自己生成的镜像

​	docker run -it c80928f6f805 /bin/bash

## **附件**：docker命令大全

![docker命令大全](https://cdn.jsdelivr.net/gh/jackmumu123/dockernote@main/pitures/20210709190504.jpg)