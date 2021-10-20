---
title: Curl
category: CLI
layout: 2017/sheet
updated: 2020-03-09
---

## Options

### Options

```bash
-o <file>    # --output: write to file
-u user:pass # --user: Authentication
```

```bash
-v           # --verbose
-vv          # Even more verbose
-s           # --silent: don't show progress meter or errors
-S           # --show-error: when used with --silent (-sS), show errors but no progress meter
```

```bash
-i           # --include: Include the HTTP-header in the output
-I           # --head: headers only
```

### Request

```bash
-X POST          # --request
-L               # follow link if page redirects
-F 	             # --form: HTTP POST data for multipart/form-data
```

### Data

```bash
-d 'data'    # --data: HTTP post data, URL encoded (eg, status="Hello")
-d @file     # --data via file
-G           # --get: send -d data via get
```

### Headers

```bash
-A <str>         # --user-agent
-b name=val      # --cookie
-b FILE          # --cookie
-H "X-Foo: y"    # --header
--compressed     # use deflate/gzip
```

### SSL

```bash
    --cacert <file>
    --capath <dir>
```

```bash
-E, --cert <cert>     # --cert: Client cert file
    --cert-type       # der/pem/eng
-k, --insecure        # for self-signed certs
```

## Examples
{: .-one-column}

```bash
# Post data:
curl -d password=x http://x.com/y
```

```bash
# Auth/data:
curl -u user:pass -d status="Hello" http://twitter.com/statuses/update.xml
```

```bash
# multipart file upload
curl -v -include --form key1=value1 --form upload=@localfilename URL

# multipart form: send data from text field and upload file
curl -F person=anonymous -F secret=@file.txt http://example.com/submit.cgi
```

```bash
# Use Curl to Check if a remote resource is available
# details: https://matthewsetter.com/check-if-file-is-available-with-curl/
curl -o /dev/null --silent -Iw "%{http_code}" https://example.com/my.remote.tarball.gz
```
```
1.1 CURL GET/HEAD
Name	Command
Curl head request	curl -I https://www.google.com
Curl head request with verbose	curl -v -I https://www.google.com
Curl with explicit http method	curl -X GET https://www.google.com
Curl without http proxy	curl --noproxy 127.0.0.1 http://www.stackoverflow.com
Curl has no timeout by default	curl --connect-timeout 10 -I -k https://www.google.com
Curl get with extra headers	curl --verbose --header "Host: www.mytest.com:8182" www.google.com
Curl get response with headers	curl -k -v https://www.google.com
```
```
1.2 CURL POST
Name	Command
Curl post request	curl -d "name=username&password=123456" <URL>
Curl post send json	curl <URL> -H "content-type: application/json" -d "{ \"woof\": \"bark\"}"
```
```
1.3 CURL ADVANCED
Name	Command
Get my public ip	curl -L -s http://ipecho.net/plain, curl -L -s http://whatismijnip.nl
Curl with credential	curl -u $username:$password http://repo.dennyzhang.com/README.txt
Curl upload	curl -v -F key1=value1 -F upload=@localfilename <URL>
Install curl in alpine linux	apk add --update curl
Curl with http2	curl -k -v --http2 https://www.google.com/
Curl ftp upload	curl -T cryptopp552.zip -u test:test ftp://10.32.99.187/
Curl ftp download	curl -u test:test ftp://10.32.99.187/cryptopp552.zip -o cryptopp552.zip
Curl upload with credential	curl -v -u admin:admin123 --upload-file package1.zip http://mysever:8081/dir/package1.zip
```
```
1.4 CURL SCRIPT
Name	Command
Install packages with curl	curl-install-package.sh
Check a website response time	curl-url-time.sh
Beautify json output for curl response	curl-format-json.sh
Curl run remote scripts	curl-remote-scripts.sh
```
```
1.5 WGET
Name	Command
Download one url	wget -O /tmp/google.html https://google.com
Download mutiple urls	wget https://google.com https://bing.com
Download a list of urls	wget -i url-list.txt, url-list.txt
```
```
1.6 MORE RESOURCES
License: Code is licencurl under MIT License.

http://curl.haxx.se
```
