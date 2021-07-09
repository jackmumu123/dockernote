## **一：容器命令**

#### 	**A.删除容器**

​	docker rm -f $(docker ps -aq)

#### 	**b.查看容器**

​	docker ps

​	c.启动容器

​	docker run -it 镜像名 /bin/bash

## **二：其他常用命令**

#### 	**A.启动镜像**

​	docker run -d   镜像名   #  $\textcolor{RedOrange}{后台运行，没有交互模式}$

​	docker run -it centos /bin/bash #$\textcolor{RedOrange}{交互模式运行，按ctrl+p+q退出}$



#### 	B.查看日志

​		docker logs -ft --tail 10 镜像名\ID

#### 	**c.查看容器中进程信息**

​		docker top 镜像名\ID

#### 	**d.查看镜像的元数据**

​	docker inspect 镜像名\ID

#### 	**e.进入当前正在运行的容器**

​	docker exec -it 镜像名\ID /bin/bash     #  $\textcolor{RedOrange}{输入exit可以退出容器}$

​	 docker attach  镜像名\ID                  #  $\textcolor{RedOrange}{进入正在运行的容器}$

#### 	**f.从容器内拷贝文件到主机上**

​	docker cp -a 容器ID:/home/test.java /root





























## **附件**：docker命令大全

![docker命令大全](https://cdn.jsdelivr.net/gh/jackmumu123/dockernote@main/pitures/20210709190504.jpg)