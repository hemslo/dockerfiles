### Usage

```
$ docker run -d -v /var/lib/scrapyd -v /var/log/scrapyd --name crawler-data busybox true
$ docker run -d --volumes-from crawler-data crawler
```
