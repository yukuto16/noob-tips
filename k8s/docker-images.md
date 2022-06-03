# k8sのdockerイメージが参照されなくて沼ったお話

## 環境
- minikube

## 解決

### レジストリコンテナなるものを作成しないとダメらしい
`docker run -d -p 5000:5000 --restart=always --name registry registry:2`

`docker images`

`docker tag <local-image-repository>:<local-image-tag> localhost:5000/<local-image-name>`

`docker push localhost:5000/<local-image-name>`

### minikube君は内部のdockerにイメージがないとダメ
環境上のdockerじゃだめ

`eval $(minikube docker-env)`