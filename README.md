# Create-SLL-Sertificat
Создание самописного SLL сертификата

# узнаём свой ip адрес
- **ip a** и во втором интерфейсе мы увидим наш ip адрес (не 127.0.0.1). Пример: 192.168.31.112

# Создаём закрытый ключ для корневого сертификата
- **openssl genrsa -des3 -out rootCA.key 2048**

# Создайте корневой сертификат, используя ключ, созданный на предыдущем шаге с помощью команды
- **openssl req -x509 -new -nodes -key rootCA.key -sha256 -days 365 -out rootCA.crt**
- **openssl genrsa -out mydomain.key 2048**
- **openssl req -new -key mydomain.key -out mydomain.csr**
- **openssl x509 -req -in mydomain.csr -CA rootCA.crt -CAkey rootCA.key -CAcreateserial -out mydomain.crt -days 365**

# Редачим apache
- **sudo nano /etc/apache2/sites–available/default–ssl.conf**
[image](https://github.com/user-attachments/assets/721933d2-59ef-4109-90d8-0b7b1e406a62)
![image](https://github.com/user-attachments/assets/fef97ca3-70b8-40a0-ba58-65c3faed541a)
- **sudo nano /etc/apache2/sites–available/000–default.conf**
![image](https://github.com/user-attachments/assets/4acd7d83-0db4-454b-94a1-e9e751c80dcb)
sudo nano /etc/nginx/sites-enabled/default
![image](https://github.com/user-attachments/assets/ce03b0e2-4b90-463f-a416-a474724dcbe1)
![Uploading image.png…]()
- **service apache2 nginx restart**
