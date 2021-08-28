Install Helm

旧バージョンのHelmコマンドを削除
```
rm -rf /usr/bin/helm
```

インストールスクリプトをダウンロードする
`curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3`{{execute}}

実行権限付与`chmod 700 get_helm.sh`{{execute}}

Helm v3のインストール`./get_helm.sh`{{execute}}

パスが通ってるディレクトリに移動`mv /usr/local/bin/helm /usr/bin/helm`{{execute}}

バージョン確認`helm version`{{execute}}

Settings Helm
