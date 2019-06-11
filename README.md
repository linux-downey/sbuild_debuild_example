## 公共部分：  

* 克隆仓库代码
  ```
  git clone https://github.com/linux-downey/sbuild_debuild_example.git
  ```    

* 源码打包
  ```
  cd sbuild_debuild_example
  tar -czvf debhello-1.0.0.tar.gz debhello-1.0.0/
  ```  

* debmake生成控制文件,如果出错，请参考<博客第二篇,debmake纠错>部分
  ```  
  cd debhello-1.0.0/
  debmake
  ```

* 编辑控制文件debian/rules,在文件中添加override，在在规则dh $@下添加一行：
  ```
  override_dh_usrlocal:
  ```

##  使用debuild的方式(接公共部分)

* 编辑控制文件debian/changelog，将第一行中的UNRELEASE修改为对应的发行版名称，ubuntu16.04为xenial。  

* 键入指令
  ```
  debuild -us -uc
  ```

## 使用sbuild的方式(接公共部分)
* 根据博客中内容创建纯净编译系统,这里创建一个ubuntu16.04的系统
  ```
  sudo sbuild-createchroot --include=eatmydata,ccache,gnupg xenial /srv/chroot/xenial-amd64-sbuild http://security.ubuntu.com/ubuntu  
  ```
* 编辑控制文件debian/changelog，将第一行中的UNRELEASE修改为ubuntu 16.04对应的xenial  
* 打包包含控制文件的源码包
  ```
  cd ..
  tar -czvf debhello-1.0.0.orig.tar.gz debhello-1.0.0/
  ```
* 编译deb包
  ```
  cd debhello-1.0.0
  sudo sbuild
  ```
