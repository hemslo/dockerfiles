### Usage

```
$ docker run -d -v /var/lib/scrapyd -v /var/log/scrapyd --name crawler-data crawler true
$ docker run -d --volumes-from crawler-data crawler
```
