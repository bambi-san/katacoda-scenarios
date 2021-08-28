HelmリポジトリからJenkinsアプリケーションをインストールする

Jenkinsのインストール（[参考](jenkins.io/doc/book/installing/kubernetes/#install-jenkins-with-helm-v3)）

JenkinsのHelmChartリポジトリ追加
`helm repo add jenkinsci https://charts.jenkins.io`{{execute}}

リポジトリ更新
`helm repo update`{{execute}}

リポジトリ一覧表示(jenkincciが表示される)
`helm repo list`{{execute}}

jenkinsアプリケーションを`jenkins-app`という名前で`default`の`namespace`にインストールする
`helm install jenkins-app jenkinsci/jenkins -n default`{{execute}}

helm list



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
