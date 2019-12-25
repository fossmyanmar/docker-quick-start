# Docker Compose

## Docker Compose

Docker Compose သည် Containers များကို Setup ပြုလုပ်ရာတွင် အသုံးပြုသည့် Tool တခုဖြစ်သည်။ Docker Compose ကိုသုံးခြင်းဖြင့် docker containers များကို Compose File တစ်ခုအနေဖြင့် ဖန်တီးနိုင်သည်။ Images and Containers များကို လည်း Signal Command ဖြင့် လွယ်ကူစွာ build လုပ်နိုင်ပါတယ်။

Docker Compose ပြုလုပ်ရန် အဆင့် \(3\) ဆင့် ရှိသည်။

* Dockerfile တွင် သုံးမည့် Services များကို သတ်မှတ်ပေးရန်
* မိမိ Enviroment အတွက် သုံးမည့် Service and Application များကို docker-file အဖြစ်ပြုလုပ်ပြီး sample.yml format ဖြင့် သိမ်းဆည်းရမည်။
* Run docker-compose up  Command ဖြင့် Docker Containers Services များကို Run နိုင်သည်။

**စက်တွင် Docker Enginer ရှိဖို့လိုပါသည်။ မရှိလျှင် Docker Engine Installation Section တွင်လေ့လာနိုင်ပါသည်။**

## Install Docker Compose

Docker Compose ကို Install ပြုလုပ်ရန် [https://github.com/docker/compose/releases](https://github.com/docker/compose/releases) \(Github Page\) တွင် ဝင်ရောက်လေ့လာ၍ ရယူနိုင်ပါသည်။

အောက်ပါ Command ဖြင့်လည်း Docker compose 1.16.1 ကို Install ပြုလုပ်နိုင်သည်။ Install မပြုလုပ်ခင် Docker versition နှင့် Specific ဖြစ်မဖြစ် စစ်ဆေးရန်လိုအပ်ပါသည်။

```text
$ curl -L https://github.com/docker/compose/releases/download/1.16.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

$ chmod +x /usr/local/bin/docker-compose
```

