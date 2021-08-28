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

`kubectl get pods -n default`{{execute}}でデプロイ結果を確認する。

serviceのPortをNodePortに編集し、NodeのPortとserviceのPortをバインドする。
`kubectl edit service/jenkins-app`{{execute}}

```
  type: ClusterIP -> NodePort
```

変更後のservice一覧表示
`kubectl get service`{{execute}}

タブを開いて8080にバインドされているport番号を指定してアクセスしてみよう。

`helm install`コマンドによりインストールされたアプリケーションはHelm独自のリポジトリでバージョン管理が行われる。
`helm list`{{execute}}コマンドでデプロイしたバージョン（Chart, AppVersion）を確認する。

`helm uninstall jenkins-app`{{execute}} でアプリケーションをアンインストールする。
