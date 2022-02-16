# Postfix Testing
## Setup DKIM
This will generate the dkim files
```
cd ./dkim
./setup.sh
```

## Setup StartTLS certs
This will generate the tls (startssl files)
```
cd ./certs
./setup.sh
```

## Start the Service
```
docker-compose up -d 
```

## Send Test Mails 
Make sure you observe the /var/log/mail.log before sending test mails!

```
docker-compose exec postfix tail -f /var/log/mail.log
```

Send mails:
```
sendemail -f "sender@mail.com" -t "recepient@domain.com" -s 127.0.0.1:25 -o tls=no -xu username -xp password -m "Nachricht" -v
```


