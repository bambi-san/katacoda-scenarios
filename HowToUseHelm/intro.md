Helmとは、Kuberntes用のパッケージマネージャのこと。

kuberntesへアプリケーションをデプロイするためには、これらのリソースをapplyすることが必要。
一つ一つapplyするのは大変。。バージョン管理も困難。。。
* Deployment
* Service
* Secret
* PersistentVolumeClaim
etc...

Helmを利用することでこれらの悩みを解消することができる。
(よく比較されるものに`kustomize`がある。)
