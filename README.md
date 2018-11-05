###Setting HTTPS/SSL up on dev

from https://github.com/jcmoraisjr/simple-ca

nagivate to nginx/dev.ssl dir

you also need openssl installed on you machine

```
docker run -d -p 80:8080 -p 443:8443 quay.io/jcmoraisjr/simple-ca

openssl req -new -newkey rsa:2048 -keyout ui-key.pem -nodes -out ui.csr -subj "/"
curl -fk --data-binary @ui.csr -o ui.pem "https://localhost/sign?cn=dev.devpledge.com&ns=dev.devpledge.com"

openssl req -new -newkey rsa:2048 -keyout api-key.pem -nodes -out api.csr -subj "/"
curl -fk --data-binary @api.csr -o api.pem "https://localhost/sign?cn=dev.api.devpledge.com&ns=dev.api.devpledge.com"

openssl req -new -newkey rsa:2048 -keyout auth-key.pem -nodes -out auth.csr -subj "/"
curl -fk --data-binary @auth.csr -o auth.pem "https://localhost/sign?cn=dev.auth.devpledge.com&ns=dev.auth.devpledge.com"

openssl req -new -newkey rsa:2048 -keyout feed-key.pem -nodes -out feed.csr -subj "/"
curl -fk --data-binary @feed.csr -o feed.pem "https://localhost/sign?cn=dev.feed.devpledge.com&ns=dev.feed.devpledge.com"
```

Then add these to your MacOSX keychain and give always trusted permissions!