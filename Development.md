## Prerequisites
- docker
- docker-compose
- VS code remote extention

#### Run below commands in dev container. You can access it using

```
sudo chown -R frappe:frappe frappe-bench
cd frappe-bench
bench new-site ims.localhost --no-mariadb-socket
bench use ims.localhost
bench --site ims.localhost install-app erpnext
bench get-app --branch v13 git@github.com:Improwised/frappe_s3_attachment.git 
bench --site ims.localhost install-app frappe_s3_attachment
bench start
```

Now visit ims.localhost:8000 in browser
