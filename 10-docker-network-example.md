# Docker Networking Example

## Docker Networking Example

Docker Network tutorial ဖက်ပြီးပြီးဆိုရင် Example လေး စမ်းလုပ်ကြည့်လို့ရပါတယ်။

ကျွန်တော် တို့ ဒီ Tutorial မှာတော့ docker containers နှစ်ခုနဲ့ docker network အသေးစားလေး တခု လုပ်ပြသွားမှာ ဖြစ်ပါတယ်။

> MySQL – A relational database server.
>
> PHPMyAdmin – A web based interface to manage MySQL server.

အခု tutorial မှာတော့ အခြား MySQL server ကို access လုပ်ဖို့အတွက် အခြား container တခုမှာ run ထားတဲ့ PHPMyAdmin ကို အသုံးပြ ပြသသွားမှာ ဖြစ်ပါတယ်။

## Network တခု Create လုပ်ခြင်း။

ပထမဦးစွာ အနေဖြင့် docker network အသစ် တခု ကို Create လုပ်ဖြစ်ပါတယ်။ my-bridge-network အမည်ရှိသော network အသစ်ကို အောက်ပါ comment အသုံးပြု ပြီး create လုပ်ပါ။

```text
  $ docker network create -d bridge my-bridge-network
```

## MySQL Container ကို Run ခြင်း။

အခု ကျွန်တော် တို့ MySQL docker container အသစ် ကို Run မှာ ဖြစ်ပါတယ်။

Default root user password အသစ်ကို သတ်မှတ်ဖို့အတွက် MYSQL\_ROOT\_PASSWORD variable ကို အောက်မှာပြထားတဲ့အတိုင်း ရိုက်ပါ။

```text
$ docker run --name mysql -e MYSQL_ROOT_PASSWORD=secret -d mysql/mysql-server
```

Container တခု create ပြီးနောက် စောစော က ကျွန်တော်တို့ create ထားတဲ့ my-bridge-network network နဲ့ ချိတ်ဆက်မှာ ဖြစ်ပါတယ်။

```text
$ docker network connect my-bridge-network mysql
```

နောက် တဆင့် အနေနဲ့ MySQL container ရဲ့ IP address အသစ် ကိုကြည့်မှာဖြစ်ပါတယ်။

```text
$ docker inspect mysql | grep "IPAddress"
```

## PHPMyAdmin Container ကို Run ခြင်း။

အခု ကျွန်တော်တို့ Docker container အသစ်ဖြစ်တဲ့ phpmyadmin ကို run မှာ ဖြစ်ပါတယ်။

MySQL ကို Run ခြင်း နောက်ဆုံးအဆင့်မှာ ရခဲ့တဲ့ MySQL container IP address ကို PMA\_HOST value အနေနဲ့ထည့်ပါမယ်။

```text
$ docker run --name phpmyadmin -d -e PMA_HOST=172.21.0.2 -p 8080:80 phpmyadmin/phpmyadmin
```

ပြီးနောက် phpmyadmin container ကို my-bridge-network ထဲ add လိုက်ပါ။

```text
$ docker network inspect my-bridge-network
```

## My-bridge-network Network ရဲ့ အချက်အလက် ကိုကြည့်ခြင်း ။

အပေါ်မှာ ပြခဲ့တဲ့ containers နှစ်ခု ကို ကျွန်တော် တို့ my-bridge-network ထဲ ထည့်ပြီးသွား တဲ့ အတွက် လက်ရှိ my-bridge-network ရဲ့ setting ကို ကြည့်လိုက်ရအောင် ။

```text
$ docker network inspect my-bridge-network
```

My-bridge-network ရဲ့ setting ကို ကြည့်ရင်တော့ အခုလိုတွေ့ရမှာဖြစ်ပါတယ်။

## Allow MySQL to PHPMyAdmin Host

MySQL default အနေနဲ့ကတော့ remote hosts connect လုပ်တာကို ခွင့်မပြုထားပါဘူး။

ဆိုတော့ ကျွန်တော် တို့ က MySQL connection အတွက် phpmyadmin ကို allow

လုပ်ပေးရမှာ ဖြစ်ပါတယ်။ MySQL container shell access ရဖို့အတွက် အောက်မှာ ပြထားတဲ့ လုပ်ရမှာဖြစ်ပါတယ်။

```text
$ docker exec -it mysql bash
```

MySQL server ထဲကို MySQL container create လုပ်တုန်းက ပေးထဲ့ခဲ့တဲ့ Password ကို အသုံးပြုပြီး Login ဝင်လိုက်ပါ။

```text
  bash-4.2# mysql -u root -p
```

phpmyadmin host ip address နဲ့ user အသစ် create လုပ်လိုက်ပါ။ ဒီ tutorial ထဲမှာတော့ phpmyadmin host ip address ကတော့ ‘**172.21.0.3**‘ ဖြစ်ပါတယ်။

```text
mysql> GRANT ALL on *.* to 'dbuser'****@****'172.21.0.3' identified by 'secret';
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> flush privileges;
Query OK, 0 rows affected (0.00 sec)

mysql> exit
Bye
```

## Access MySQL with PHPMyAdmin

နောက်ဆုံးအနေဖြင့် ကျွန်တော် တို့ ရဲ့ docker host system က port 8080 မှ တဆင့် phpmyadmin web user interface ကို ချိတ်ဆက်လို့ ရသွားပါတယ်။

phpMyAdmin ကို MySQL ရဲ့ အချက်အလက်တွေ သုံးပြီး အပေါ်မှာ ပြထားတဲ့ အတိုင်း Login ဝင်ရန် အသုံးပြုလို့ရပါတယ်။

