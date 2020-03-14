# Apache Tika の実験

## 準備
念のため、私の Docker のバージョン確認する。
```
% docker version                        
Client: Docker Engine - Community
 Version:           19.03.8
 API version:       1.40
 Go version:        go1.12.17
 Git commit:        afacb8b
 Built:             Wed Mar 11 01:21:11 2020
 OS/Arch:           darwin/amd64
 Experimental:      false

Server: Docker Engine - Community
 Engine:
  Version:          19.03.8
  API version:      1.40 (minimum version 1.12)
  Go version:       go1.12.17
  Git commit:       afacb8b
  Built:            Wed Mar 11 01:29:16 2020
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          v1.2.13
  GitCommit:        7ad184331fa3e55e52b890ea95e65ba581ae3429
 runc:
  Version:          1.0.0-rc10
  GitCommit:        dc9208a3303feef5b3839f4323d9beb36df0a9dd
 docker-init:
  Version:          0.18.0
  GitCommit:        fec3683
```

## セットアップ
次のサイト通りに手順を実行する。
  - https://hub.docker.com/r/apache/tika

1. Docker image を取得する。
    ```
    % docker pull apache/tika
    ```

2. 起動する。
    ```
    % docker run -d -p 9998:9998 apache/tika
    ```


## 実験
何かファイルを与えてみる。
```
% curl -T data/Book1.xlsx http://localhost:9998/tika
Sheet1
        manaBrain Retriever は素晴らしいクラウドサービスです。 スバラシイ 


Sheet2
        #       サービス
        1       manaBbrain
        2       manaBrain Retriever
        3       追い風 オイカゼ 


```
「スバラシイ」、「オイカゼ」は Tika が付与したのだろうか？
