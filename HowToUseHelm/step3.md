Helm Chartを作ってクラスタに適用してみよう(nginx)

Chartのテンプレートを作成する。

`helm create app`{{execute}}

`cd app`{{execute}}

`values.yaml`ファイルを修正する(imageはnginxになっているためそのまま)。
`vi values.yaml`{{execute}}

```yaml
service:
  type: NodePort
  port: 80
```

`helm lint .`{{execute}} コマンドを実行してlintかける。

helm chartの展開結果(manifest)を表示する（リリース名を`nginx`とする）。

`helm template --release-name nginx .`{{execute}}

### インストール（適用）方法

#### `helm install` コマンドを利用したインストール

`cd ..`{{execute}}

作成したhelm chartをパッケージ化する。
`helm package app`{{execute}}

コマンドを実行すると同一パスに`.tgz`の拡張子がついたファイルが作成される。

`helm install`コマンドを利用するときは必ずChartをパッケージ化`.tgz`が必要。

`Chart作成(or 修正) -> パッケージ化 -> リポジトリにPush`しChartとアプリケーションのバージョンを管理する。

今回はローカルで管理する。
管理用ファイル（index.yaml）を生成する。

```
mkdir charts
mv *.tgz charts/
helm repo index charts
```{{execute}}

`charts/index.yaml`にhelmのパッケージ管理情報が記載されている。

インストールする
`helm install nginx charts/app-0.1.0.tgz -n default`{{copy}}

適用後確認
`helm list`{{execute}}
`kubectl get pods -n default`

アンインストール
`helm uninstall nginx`{{execute}}


#### helm template　の結果をapplyする

ArgoCDを利用したアプリケーションのリリースはこの方法が利用されている。

helm chartの展開結果(manifest)をクラスタに適用する。
(上記の結果をyamlファイルに保存し`kubectl apply -f {ファイルパス}`するのと同じ)

`helm template --release-name nginx . | kubectl apply -f -`{{execute}}

nginxのNodePortの番号を確認する。
`kubectl get svc/nginx-app -n default`{{execute}}

`View HTTP port 80 on Host 1`を実行しport番号をNodeの番号(`3xxxx`)に変更しアクセスする。

リソースを削除するとき。
`helm template --release-name nginx . | kubectl delete -f -`

