流量从入口到Ingress Controller的pod有下面几种方式

type为LoadBalancer的时候手写externalIPs很鸡肋,后面会再写文章去讲它

type为LoadBalancer的时候只有云厂商支持分配公网ip来负载均衡,LoadBalancer 公开的每项服务都将获得自己的 IP 地址,但是需要收费,且自己建立集群无法使用

不创建svc,pod直接用hostport,效率等同于hostnetwork,如果不代理四层端口还好,代理了需要修改pod的template来滚动更新来让nginx bind的四层端口能映射到宿主机上

Nodeport,端口不是web端口(但是可以修改Nodeport的范围改成web端口),如果进来流量负载到Nodeport上可能某个流量路线到某个node上的时候因为Ingress Controller的pod不在这个node上,会走这个node的kube-proxy转发到Ingress Controller的pod上,多走一趟路

不创建svc,效率最高,也能四层负载的时候不修改pod的template,唯一要注意的是hostnetwork下pod会继承宿主机的网络协议,也就是使用了主机的dns,会导致svc的请求直接走宿主机的上到公网的dns服务器而非集群里的dns server,需要设置pod的dnsPolicy: ClusterFirstWithHostNet即可解决
