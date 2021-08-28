Helm v3をインストールする

Helm v2とHelm v3では利用方法が大きく異なるため要注意。
[参考(Helm2 からの変更点)](https://helm.sh/ja/docs/faq/#helm-2-%E3%81%8B%E3%82%89%E3%81%AE%E5%A4%89%E6%9B%B4%E7%82%B9)


Helm v3インストールスクリプトをダウンロードする
`curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3`{{execute}}

実行権限付与する
`chmod 700 get_helm.sh`{{execute}}

Helm v3をインストールする
`./get_helm.sh`{{execute}}

パスが通ってるディレクトリに移動する
`mv /usr/local/bin/helm /usr/bin/helm`{{execute}}

バージョン確認(Helm v3以上になってる)
`helm version`{{execute}}

