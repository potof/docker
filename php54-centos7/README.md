
```bash
docker rm test
docker rmi php54-centos7

docker build --tag php54-centos7 . --no-cache
docker run -d --name test php54-centos7

docker save php54-centos7 -o php54-centos7.tar
```



https://ptsv.jp/2017/06/21/centos-%E3%81%8B%E3%82%89-windows%E4%B8%8A%E3%81%AEsqlserver%E3%81%B8%E3%81%AE%E9%81%93%E3%81%AE%E3%82%8A/

