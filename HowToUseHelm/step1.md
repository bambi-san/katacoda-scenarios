Install Helm


[Helmコマンドチートシート](https://helm.sh/docs/helm/helm/)

旧バージョンのHelmコマンドを削除
```
rm -rf /usr/bin/helm
```

インストールスクリプトをダウンロードする
`curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3`{{execute}}

実行権限付与する
`chmod 700 get_helm.sh`{{execute}}

Helm v3をインストールする
`./get_helm.sh`{{execute}}

パスが通ってるディレクトリに移動する
`mv /usr/local/bin/helm /usr/bin/helm`{{execute}}

バージョン確認(Helm v3以上になってる)
`helm version`{{execute}}


Jenkinsのインストール（[参考](jenkins.io/doc/book/installing/kubernetes/#install-jenkins-with-helm-v3)）

JenkinsのHelmChartリポジトリ追加
`helm repo add jenkinsci https://charts.jenkins.io`{{execute}}

リポジトリ更新
`helm repo update`{{execute}}

リポジトリ一覧表示(jenkincciが表示される)
`helm repo list`{{execute}}

インストール
`helm install jenkinsci/jenkins`{{execute}}

Jenkins公開設定

service一覧表示
`kubectl get service`{{execute}}

ClisterIPをNodePortに変更する

`kubectl edit service/{sesrvice名}`

```
  type: ClusterIP -> NodePort
```

変更後のservice一覧表示
`kubectl get service`{{execute}}

タブを開いて8080にバインドされているport番号を指定してアクセスしてみよう。









