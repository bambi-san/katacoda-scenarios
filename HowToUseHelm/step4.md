`values.yaml`のデータを環境ごとに上書きする

`cd app`{{execute}}

`vi values-stable.yaml`{{execute}}

```yaml
replicaCount: 99

image:
  repository: nginx
  pullPolicy: IfNotPresent
  # Overrides the image tag whose default is the chart appVersion.
  tag: "stable"
```

`--values`オプションを指定するとvalues.yamlが指定したファイルで上書きされたmanifestが出力される。

`helm template --release-name nginx --values values-stable.yaml .`{{execute}}
