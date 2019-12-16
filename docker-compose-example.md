# Docker Compose Example

## Docker Compose Example File

Docker Composer file သည် docker-compose.yml \(format\) ဖြစ်ပြီး အောက်တွင် Version 3 docker composer file ကို Sample ပြထားသည်။ ဤ File သည်  
Sample ဖြစ်၍ Service တခုဖြစ်သည့် WEB Name တစ်ခုကိုသာ ပြထားသည်။

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

Docker Compose နှင့် Docker Container များကို manage ပြုလုပ်ရန်အတွက် docker-compose command ကိုလည်း subcommand အဖြင့် provides လုပ်ပေးသည်။

အောက်တွင့် Subcommand အချို့ကို လေ့လာနိုင်သည်။ သတိပြုရန်မှာ Container Name နှင့် Services name ကို မမှားဖို့ သတိပြုရမည်။

`build -` build option ဖြင့် images များကို build လုပ်ပြီး Services များကို အသုံးပြုနိုင်သည်။

```text
$ docker-compose build             ## Build all services
$ docker-compose build web         ## Build single service
```

`up –` Current Directory အောက်ရှိ docker-composer.yml မှ docker container နှင့် Services များကို Create ပြုလုပ်ရန်ဖြစ်သည်။ \( -d \) Switch သည် Container ကို daemon mode ဖြင့် run စေရန်ဖြစ်သည်။

```text
$ docker-compose up -d            ## Create all containers
$ docker-compose up -d web        ## Create single container
```

`down –` ဤ Option သည် containers များ၏ Neteork, Container Service and Associate Images များကို ရပ်ရန်, ဖျက်ရန် အသုံးပြုနိုင်သည်။

```text
$ docker-compose down           ## Restart all containers
$ docker-compose down web       ## Restart single container
```

`ps –` Container များ၏ Services,Status and Port များ၏ process detail ကို သိနိုင်ရန် သုံးသည်။

```text
$ docker-compose ps
```

`exec –` Running Containers များကို exec ပြုလုပ်ရန်သုံးသည်။ For example, Web Service Run နေသည့် Container ကို list-file အနေဖြင့် ကြည့်ရန်..

```text
$ docker-compose exec web ls -l
```

`start -` Containers များကို Start လုပ်ရန်သုံးသည်။

```text
$ docker-compose start            ## Start all containers
$ docker-compose start web        ## Start single container
```

`stop -` Running Containers များကို ရပ်လိုက်ရန် အသုံးပြုသည်။

```text
$ docker-compose stop             ## Stop all containers
$ docker-compose stop web         ## Stop single container
```

```text
`restart –`
    Containers များကို restart ပြုလုပ်ရန် သုံးသည်။
```

```text
$ docker-compose restart           ## Restart all containers
$ docker-compose restart web       ## Restart single container
```

```text
`paue -`
    Running Containers များကို paue လုပ်ရန်သုံးသည်။
```

```text
$ docker-compose pause            ## Start all paused containers
$ docker-compose pause web        ## Start single paused container
```

`rm –` Containers များကို ဖျက်ရန်, ဖယ်ရှားရန်သုံးသည်။

```text
$ docker-compose rm               ## Start all paused containers
$ docker-compose pause web        ## Start single paused container
```

