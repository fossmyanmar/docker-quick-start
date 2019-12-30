# Docker Compose

## Docker Compose

Docker Compose ဟာဆိုရင် Containers များကို Setup ပြုလုပ်ရာတွင် အသုံးပြုသည့် Tool တစ်ခုဖြစ်ပါတယ်။ Docker Compose ကိုသုံးခြင်းဖြင့် docker containers များကို Compose File တစ်ခုအနေဖြင့် ဖန်တီးနိုင်ပါတယ်။ Images and Containers များကို လည်း Single Command ဖြင့် လွယ်ကူစွာ build လုပ်နိုင်ပါတယ်။

Docker Compose ပြုလုပ်ရန် အဆင့် \(3\) ဆင့် ရှိပါတယ်။

* Dockerfile တွင် သုံးမည့် Services များကို သတ်မှတ်ပေးရမယ်။
* မိမိ Enviroment အတွက် သုံးမည့် Service and Application များကို docker-file အဖြစ်ပြုလုပ်ပြီး sample.yml format ဖြင့် သိမ်းဆည်းရမယ်။
* Run docker-compose up  Command ဖြင့် Docker Containers Services များကို Run နိုင်ပါတယ်။

**စက်တွင် Docker Enginer ရှိဖို့လိုပါသည်။ မရှိလျှင် Docker Engine Installation Section တွင်လေ့လာနိုင်ပါသည်။**

## Install Docker Compose

Docker Compose ကို Install ပြုလုပ်ရန် [https://github.com/docker/compose/releases](https://github.com/docker/compose/releases) \(Github Page\) တွင် ဝင်ရောက်လေ့လာ၍ ရယူနိုင်ပါတယ်။

အောက်ပါ Command ဖြင့်လည်း Docker compose 1.16.1 ကို Install ပြုလုပ်နိုင်ပါတယ်။ Install မပြုလုပ်ခင် Docker version နှင့် Specific ဖြစ်မဖြစ် စစ်ဆေးရန်လိုအပ်ပါတယ်။

```text
$ curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

$ chmod +x /usr/local/bin/docker-compose
```

## Docker Compose Example File

Docker Composer file ဟာ docker-compose.yml \(format\) ဖြစ်ပြီး အောက်တွင် Version 3 docker composer file ကို Sample ပြထားပါတယ်။ ယခု File ဟာဆိုရင် Sample Service တစ်ခုဖြစ်သည့် WEB Name တစ်ခုကိုသာ ပြထားပါတယ်။

```text
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
        build: .
        container_name: apache_web
        restart: always
        ports:
            - "8080:80"
```

## Docker Compose CLI Reference

Docker Compose နှင့် Docker Container များကို manage ပြုလုပ်ရန်အတွက် docker-compose command ဟာ subcommand များကိုလည်း provides လုပ်ပေးပါတယ်။

အောက်တွင် subcommand အချို့ကို လေ့လာနိုင်ပါတယ်။ သတိပြုရန်မှာ Container Name နှင့် Services Name ကို မမှားဖို့ သတိပြုရမှာဖြစ်ပါတယ်။

`build -` build option ဖြင့် images များကို build လုပ်ပြီး Services များကို အသုံးပြုနိုင်ပါတယ်။

```text
$ docker-compose build             ## Build all services
$ docker-compose build web         ## Build single service
```

`up –` Current Directory အောက်ရှိ docker-composer.yml မှ docker container နှင့် Services များကို Create ပြုလုပ်ရန်ဖြစ်ပါတယ်။
\( -d \) Switch ဟာဆိုရင် Container ကို daemon mode ဖြင့် run စေရန်ဖြစ်ပါတယ်။

```text
$ docker-compose up -d            ## Create all containers
$ docker-compose up -d web        ## Create single container
```

`down –` Option ကို containers များ၏ Network, Container Service and Associate Images များကို ရပ်ရန်, ဖျက်ရန် အသုံးပြုနိုင်ပါတယ်။

```text
$ docker-compose down           ## Restart all containers
$ docker-compose down web       ## Restart single container
```

`ps –` Container များ၏ Services, Status and Port များ၏ process detail ကို သိနိုင်ရန် သုံးပါတယ်။

```text
$ docker-compose ps
```

`exec –` Running Containers များကို exec ပြုလုပ်ရန်သုံးပါတယ်။ For example, Web Service Run နေသည့် Container ကို list-file အနေဖြင့် ကြည့်ရန်..

```text
$ docker-compose exec web ls -l
```

`start -` Containers များကို Start လုပ်ရန်သုံးပါတယ်။

```text
$ docker-compose start            ## Start all containers
$ docker-compose start web        ## Start single container
```

`stop -` Running Containers များကို ရပ်လိုက်ရန် အသုံးပြုပါတယ်။

```text
$ docker-compose stop             ## Stop all containers
$ docker-compose stop web         ## Stop single container
```

`restart –`

```text
    Containers များကို restart ပြုလုပ်ရန် သုံးပါတယ်။
```

```text
$ docker-compose restart           ## Restart all containers
$ docker-compose restart web       ## Restart single container
```

`pause –` Containers များကို pause လုပ်ရန် သုံးပါတယ်။

```text
$ docker-compose pause            ## Start all paused containers
$ docker-compose pause web        ## Start single paused container
```

`rm –` Containers များကို ဖျက်ရန်, ဖယ်ရှားရန် သုံးပါတယ်။

```text
$ docker-compose rm               ## Start all paused containers
$ docker-compose pause web        ## Start single paused container
```

