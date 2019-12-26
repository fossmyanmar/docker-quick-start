# Docker Compose Example

### Step 1 – Create Directory Structure 

ပထမဆုံး အနေဖြင့် docker compose အမည်ရှိ directory တစ်ခု တည်ဆောက်ပါမည်။ ထို့နောက် web application သိမ်းဆည်းရန် webapp အမည်ရှိ directory တည်ဆောက်ပါမည်။ webapp directory ထဲတွင် web application ကိုစမ်းရန် အတွက် index.html ကို တည်ဆောက်ပါမည်။

```
$ mkdir dockercompose && cd dockercompose
$ mkdir webapp && echo "It Works"; webapp/index.html
```

### Step 2 – Create Dockerfile for Webapp 

ပြီးနောက် web application အတွက် လိုအပ်သော dockerfile ကို webapp directory ထဲမှာတည်ဆောက်ပါမည်။  dockerfile သည် web application အတွက် လိုအပ်သော apache web server ပါ၀င်သည့် customized image တည်ဆောက်ရန်ဖြစ်ပါသည်။ 

```text
$ vim  webapp/Dockerfile
```

ထို့နောက် အောက်ပါ code များကို ပေါင်းထည့်ပါ။

```text
FROM tecadmin/ubuntu-ssh:16.04

RUN apt-get update \
   && apt-get install -y apache2

COPY index.html /var/www/html/
WORKDIR /var/www/html
CMD ["apachectl", "-D", "FOREGROUND"]
EXPOSE 80
```

### Step 3 – Create Docker Compose File

ထို့နောက် လက်ရှိ directory ထဲတွင် docker-compose.yml အမည်ရှိ docker configuration ဖိုင် တစ်ခုကို တည်ဆောက်ပါမည်။ ထို configuration ဖိုင် သည် အသုံးပြုမည့် containers အကုန်လုံးကို ကိုယ်စားပြုမည်ဖြစ်သည်။

```text
$ vim  docker-compose.yml
```

ထို့ နောက် အောက် ပါ code များကို ပေါင်းထည့်ပါ။

```
version: '3'
services:
  db:
     image: mysql
     container_name: mysql_db
     restart: always
     environment:
        - MYSQL_ROOT_PASSWORD="secret"
  web:
    image: apache
    build: ./webapp
    depends_on:
       - db
    container_name: apache_web
    restart: always
    ports:
      - "8080:80"
```

အထက်ပါ ဖိုင်သည် containers နှစ်ခု အတွက်ဖြစ်သည်။ ပထမ container သည် mysql database server အတွက်ဖြစ်ပြီး ဒုတိယသည် web server အတွက်ဖြစ်သည်။ Web container သည် application များကို apache server တွင် အလုပ်လုပ်စေမည်ဖြစ်သည်။ webapp directory ကို build directory အဖြစ် သတ်မှတ်ထားခြင်းဖြစ်သည်။

### Step 4 – Build Webapp Image 

အောက်ပါ command ဖြင့် webapp directory အတွင်းရှိ contents များနှင့် Dockerfile ကို အသုံးပြု၍ apache အမည်ရှိ image တစ်ခုကို တည်ဆောက်ပါမည်။

```text
$ docker-compose build
```



> ```text
> db uses an image, skipping
> Building web
> Step 1/6 : FROM tecadmin/ubuntu-ssh:16.04
> 16.04: Pulling from tecadmin/ubuntu-ssh
> b3e1c725a85f: Pull complete
> 4daad8bdde31: Pull complete
> 63fe8c0068a8: Pull complete
> 4a70713c436f: Pull complete
> bd842a2105a8: Pull complete
> c41407f48fa7: Pull complete
> 1fcfeb9b5ef4: Pull complete
> 13195a7d2240: Pull complete
> b86be64bbda8: Pull complete
> 8c951fe917dc: Pull complete
> f74bc80103b6: Pull complete
> Digest: sha256:523d6fbc97954e9f77231bf54bfcfbbdd4805349887477fbac4a63dc735d777d
> Status: Downloaded newer image for tecadmin/ubuntu-ssh:16.04
>  ---> bb63b492da01
> Step 2/6 : RUN apt-get update    && apt-get install -y apache2
>  ---> Running in 00be0dd717ce
> [[[Removed long output from here]]]
>  ---> 41c731590234
> Removing intermediate container 00be0dd717ce
> Step 3/6 : COPY index.html /var/www/html/
>  ---> 42f84d4c2243
> Removing intermediate container 945aaee6cbde
> Step 4/6 : WORKDIR /var/www/html
>  ---> 40bebd21e352
> Removing intermediate container e13f5f412906
> Step 5/6 : CMD apachectl -D FOREGROUND
>  ---> Running in ab0db1ef1c6e
>  ---> 587bf2323289
> Removing intermediate container ab0db1ef1c6e
> Step 6/6 : EXPOSE 80
>  ---> Running in 7bcbef52d585
>  ---> 8f03d4135394
> Removing intermediate container 7bcbef52d585
> Successfully built 8f03d4135394
> Successfully tagged apache:latest
> ```

### Step 5 – Launch Docker Containers 

docker-compose up ကို အသုံးပြု၍ containers များကို စတင်စေမည်။ Daemon mode ကို အသုံးပြုရန် -d option ကို အသုံးပြုနိုင်သည်။

```text
$ docker-compose up -d
```

### Step 6 – Update Content in Web Application <a id="step-6-&#x2013;-update-content-in-web-application"></a>

Web application တွင် ပြောင်းလဲမှု များပြုလုပ်လိုလျှင်

```text
$ echo "Welcome to Docker Compose Tutorial" >> webapp/index.html
```

ပြီးလျှင် အောက်ပါ command များကို သုံး၍ webapp container ကို ပြန်လည် တည်ဆောက်ပြီး စတင် အလုပ်လုပ်စေနိုင်ပါသည်။

```text
$ docker-compose build
$ docker-compose up -d
```



 

