# K8S 
## K8S安装步骤

### 配置并安装k8s国内源
    1. 创建配置文件 
    sudo touch /etc/apt/sources.list.d/kubernetes.list
    2. 添加写权限
    sudo chmod 666 /etc/apt/sources.list.d/kubernetes.list 
    3. 再添加，内容如下:
    deb http://mirrors.ustc.edu.cn/kubernetes/apt kubernetes-xenial main
    执行sudo apt update 更新操作系统源，开始会遇到如下错误：
       The following signatures couldn't be verified because the public key is not available:
       NO_PUBKEY FEEA9169307EA071 NO_PUBKEY 8B57C5C2836F4BEB
    签名认证失败，需要重新生成。记住上面的NO_PUBKEY 8B57C5C2836F4BEB
    
    4. 运行如下命令，添加错误中对应的key(错误中NO_PUBKEY后面的key的后8位)：
    gpg --keyserver keyserver.ubuntu.com --recv-keys 836F4BEB
    
    5. 接着运行如下命令，确认看到OK，说明成功，之后进行安装:
    gpg --export --armor 836F4BEB | sudo apt-key add -
   
    6. 再次重新运行 sudo apt update 更新系统下载源数据列表

    
