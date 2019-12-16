# Docker Container

## Docker Container

Docker container ဆိုတာ docker image တစ်ခုကို run လိုက်တဲ့အခါမှာ တည်ဆောက်လိုက်တဲ့ instance လေးတစ်ခုပဲ ဖြစ်ပါတယ်။ Container တစ်လုံးဟာ application တွေကို အလုပ်လုပ်စေဖို့အတွက်လိုအပ်တဲ့ libraries တွေနဲ့ setting တွေကိုသာ ပေါင်းစပ်ဖွဲ့စည်းထားတာ ဖြစ်ပါတယ်။ အဲ့ဒါဟာ Application တစ်ခုအတွက် အရမ်းကိုပေ့ါးပါးပြီး အလွယ်တစ်ကူရွှေ့ပြောင်းလို့ရ လောက်အောင် သေးငယ်တဲ့ environment တစ်ခုပဲ ဖြစ်ပါတယ်။

## Run Docker Container

System ပေါ်မှာ Docker Container တစ်လုံးကို စတင်မောင်းနှင်ရန်အတွက် docker run command ကို အသုံးပြုပါတယ်။ ဥပမာအားဖြင့် - အောက်ပါ command ကိုရိုက်လျှင် hello-world image ကိုအသုံးပြု၍ docker container တစ်လုံးကို တည်ဆောက်ပါလိမ့်မယ်။

```text
$ docker run hello-world
```

အခု .. CentOS operating system ကို အသုံးပြုပြီးတေ့ာ အလုပ်လုပ်နေမယ့် docker container တစ်လုံးကို တည်ဆောက်ပါမယ်။ -it ဆိုတဲ့ option က pseudo-TTY အသုံးပြုလို့ရတဲ့ interactive session တစ်ခုကို ပေးပါတယ်။ အဲ့ဒီကနေ container shell ကို ချက်ချင်းသုံးလို့ရပါလိမ့်မယ်။

```text
$ docker run -it centos
```

![](https://lh5.googleusercontent.com/w3zCpCpXI0XwXUEOqgGpwxTuviBiViOgrnb8k-RfcbnJVZR_SJRsmehhsFOWQBQralbho3euxGiCzvJ1kX0Lbg24IsoFGifUuiyHPn6ZDDFsqeQB8j_czCEDi4luPbsaTevRz7M)

ကျွန်တော်တို့ customized လုပ်ထားတဲ့ ssh access enabled လုပ်ထားတဲ့ Ubuntu docker image ကိုလည်း [docker hub repository](https://hub.docker.com/r/tecadmin/ubuntu-ssh/) မှာ စမ်းကြည့်လို့ရပါတယ်။

```text
$ sudo docker run -d -p 2222:22 tecadmin/ubuntu-ssh:16.04
```

## List Docker Containers

လက်ရှိ System ပေါ်မှာ အလုပ်လုပ်နေတဲ့ containers တွေအားလုံးကို list ထုတ်ကြည့်ချင်ရင် docker ps command ကိုသုံးပါတယ်။ အဲဒီ command က ရပ်ထားတဲ့ container တွေကိုတော့ list ထုတ်ပြမှာ မဟုတ်ပါဘူး။ အဲ့ဒါက Container ID, Container နာမည် နဲ့ container နဲ့ပတ်သက်တဲ့ အခြားအသုံးဝင်တဲ့ information တွေကိုပါ ပြပေးမှာဖြစ်ပါတယ်။

```text
$ docker ps
```

အပေါ်က command မှာ -a ဆိုတဲ့ option ကိုပါ ထည့်သုံးမယ်ဆိုရင်တော့ ရပ်ထားတဲ့ container တွေကိုပါ list ထုတ်ပြပေးမှာဖြစ်ပါတယ်။

```text
$ docker ps -a
```

![](https://lh5.googleusercontent.com/-9Ml2Bau6CsIIzIYj4-YKTG5QpHaW6qVec9k0Wc8JMqFe2qcsXcswczPsm4PySkySiKxYT7T_USa8RxH2u9n64KnlODb2tiddwaLHzA_uIb6EtExbPMJx2ZKq4Jxgy9NsGxR-VE)

## Find all Details of Container

Docker container တစ်လုံးနဲ့ပတ်သက်တဲ့ အသေးစိတ်အချက်အလက်အားလုံးကို ရှာချင်တဲ့အခါမှာတော့ docker inspect command ကို အသုံးပြုပါတယ်။ Container ရဲ့ အသေးစိတ်အချက်အလက်တွေကို သိချင်တယ်ဆိုရင်တော့ ကိုယ်သိချင်တဲ့ container ရဲ့ container ID သို့မဟုတ် container နာမည်ကို တိတိကျကျထည့်ပေးရမှာဖြစ်ပါတယ်။

```text
$ docker inspect cc5d74cf8250
```

## Delete Docker Container

System ထဲမှာရှိနေတဲ့ docker container ကို ဖျက်ချင်တယ်ဆိုရင်တော့ docker rm command ကို အသုံးပြုပါတယ်။ Container ကိုဖျက်ချင်တယ်ဆိုရင်တော့ ကိုယ်ဖျက်ချင်တဲ့ container ရဲ့ container ID သို့မဟုတ် container နာမည်ကို တိတိကျကျထည့်ပေးရမှာဖြစ်ပါတယ်။

```text
$ docker stop cc5d74cf8250
$ docker rm cc5d74cf8250
```

