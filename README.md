# Flask-ubuntu-server-instalation

```bash
git clone https://github(yang anda tuju di sini saya menggunakan encrypt milik saya yaitu encrypt)
```
```bash
ls
cd encrypt
```
## untuk mengsetting database
```bash
cd database
```
```bash
ls
pwd
```
### kita lewati dahulu untuk mysql!!!!

## lanjut setting apache2
```bash
cd /etc/apache2
ls
```
```bash
cd sites-available/
ls
```
```bash
pwd
```
```bash
sudo cp 000-default.conf /etc/apache2/sites-available/000-default.conf.bak
```
```bash
ls
```
terdapat 3 file

```bash
sudo mv 000-default.conf /etc/apache2/sites-enabled/
```
```bash
cd /etc/apache2/sites-enabled
ls
```
```bash
sudo chmod 755 000-default.conf
ls
```
```bash
sudo nano /etc/apache2/sites-enabled/000-default.conf
```
### isi dengan konfigurasi
```bash
<VirtualHost *:80>
    ServerName your-domain.com
    ServerAdmin admin@your-domain.com

    ProxyPreserveHost On
    ProxyPass / http://127.0.0.1:8000/
    ProxyPassReverse / http://127.0.0.1:8000/

    ErrorLog ${APACHE_LOG_DIR}/flask_app_error.log
    CustomLog ${APACHE_LOG_DIR}/flask_app_access.log combined
</VirtualHost>
```
```bash
sudo apache2ctl configtest
```
```bash
sudo systemctl restart apache2
```
```bash
sudo nano /etc/apache2/sites-enabled/000-default.conf
```
jika di configtest syntax belum OK maka lakukan
```bash
sudo a2enmod proxy
sudo systemctl restart apache2
```
```bash
sudo a2enmod proxy_http
sudo systemctl restart apache2
```
tes kembali dan pastikan syntax OK
```bash
sudo apache2ctl configtest
```
## masuk ke folder encryp lagi
### install flask dan gunicorn
```bash
sudo apt install python3-flask
```
```bash
sudo apt install gunicorn
```
## anda dapat mejalankan web server anda dengan perintah
```bash
gunicorn -b '127.0.0.1:8000' app:app 
```
