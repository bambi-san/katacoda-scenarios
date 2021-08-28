Install Helm

旧バージョンのHelmコマンドを削除
```
rm -rf /usr/bin/helm
```

Helm v3.0をインストールする
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3

chmod 700 get_helm.sh
./get_helm.sh

mv /usr/local/bin/helm /usr/bin/helm

helm version
```


Settings Helm
