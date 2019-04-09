jb 安装：

go get github.com/jsonnet-bundler/jsonnet-bundler/cmd/jb

jsonnet安装：

go get github.com/google/go-jsonnet/jsonnet

go get github.com/brancz/gojsontoyaml

$ mkdir my-kube-prometheus; cd my-kube-prometheus

$ jb init # Creates the initial/empty `jsonnetfile.json` # Install the kube-prometheus dependency

$ jb install github.com/coreos/prometheus-operator/contrib/kube-prometheus/jsonnet/kube-prometheus # Creates `vendor/` & `jsonnetfile.lock.json`, and fills in `jsonnetfile.json`
新增es的数据源： vendor/grafana/grafana.libsonnet

邮件报警配置路径在：/root/my-kube-prometheus/vendor/kube-prometheus/alertmanager
