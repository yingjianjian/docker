# 加入了密码 需要根据自己的情况修改redis.conf文件
#加入集群   redis-trib.rb 不支持域名 需要解析
ruby redis-trib.rb create --replicas 1 \
  `dig +short redis-app-0.redis-service.middleware.svc.cluster.local`:6379 \
  `dig +short redis-app-1.redis-service.middleware.svc.cluster.local`:6379 \
  `dig +short redis-app-2.redis-service.middleware.svc.cluster.local`:6379 \
  `dig +short redis-app-3.redis-service.middleware.svc.cluster.local`:6379 \
  `dig +short redis-app-4.redis-service.middleware.svc.cluster.local`:6379 \
  `dig +short redis-app-5.redis-service.middleware.svc.cluster.local`:6379

