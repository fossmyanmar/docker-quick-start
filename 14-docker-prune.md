# Docker Prune

## Prune Objects in Docker

ပုံမှန်ဆို docker ကသူအသုံးမပြုတော့တဲ့ objects ‌တွေကို သူ့ကိုဖျက်ပါလို့မပြောမချင်း မဖျက်ဘဲ ဒီတိုင်းထားထားတတ်ပါတယ်။ ဒီနေရာမှာ objects ဆိုတာ docker နဲ့ဆိုင်တဲ့ images, containers, volumes နဲ့ network တို့ကိုပြောတာပါ။ ဒါကြောင့် သူ့မှာ unused objects တွေကိုဖျက်ပစ်ဖို့အတွက် option တစ်ခုထည့်ပေးထားပါတယ်။ ဒါကတော့ docker prune ဆိုတဲ့ command ပါ။ 

**Syntax:**

```bash
$ docker [object] prune [options]
```

### Prune all unused Objects.

အောက်က command ကတော့ docker က အသုံးမပြုတော့တဲ့ container, image, volume နဲ့ network တွေကို ဖယ်ရှားပေးပါလိမ့်မယ်။

```bash
$ docker system prune
```

`--‌all option` ကတော့ unused ဖြစ်နေတဲ့ docker နဲ့ပါတ်သတ်တာအကုန်ကိုဆိုလိုတာပါ။

```bash
$ docker system prune --all
```

`--filter` ဆိုတဲ့ option ကတော့ key=value နဲ့တွဲသုံးရပါတယ်။ ဥပမာ အောက်က command က until=24 hours ဆိုတာကလွန်ခဲ့တဲ့ 24 နာရီမတိုင်ခင်က build ခဲ့တဲ့ images တွေ၊ stop ဖြစ်နေတဲ့ containers တွေ ၊ အသုံးမပြုတော့တဲ့ network တွေကိုဖျက်ပစ်မယ်လို့ပြောတာပါ။

```bash
$ docker system prune --filter "until=24h"
```

### Prune Images

အောက်က command ကိုတော့ Unused images တွေကိုပဲရွေးဖျက်ချင်တယ်ဆိုရင်သုံးလို့ရပါတယ်။

```bash
$ docker image prune
```

### Prune containers

Stop/exited ဖြစ်သွားတဲ့ Containers တွေကိုပဲရွေးဖျက်ချင်ရင်တော့ အောက်က command ကိုသုံးလို့ရပါတယ်။

```bash
$ docker container prune
```

### Prune Volume

အသုံးမပြုတော့တဲ့ volumes တွေကိုဖျက်ချင်တဲ့အခါမှာက အောက်ကလိုမျိုး သုံးနိုင်ပါတယ်။

```bash
$ docker volume prune
```

### Prune Network

အပေါ်က command တွေလိုပဲ network တွေကိုဖယ်ရှားချင်တဲ့အခါမှာလည်း prune ကိုအသုံးပြုနိုင်ပါတယ်။

```bash
$ docker network prune
```

### Conclusion

Yes or No question တွေမပေးဘဲ တန်းဖျက်ချင်တာသေချာတယ်ဆိုရင်တော့ အနောက်ကနေ force option အနေနဲ့ -f ကိုအသုံးပြုပြီးဖျက်နိုင်ပါတယ်။

```bash
$ docker system prune -f
$ dokcer image prune -f
$ docker container prune -f
$ docker network prune -f
$ docker volume prune -f
```

Options တွေကိုအခြေအနေအပေါ်မူတည်ပြီးတော့လည်း ကိုယ့်စိတ်ကြိုက် တွဲသုံးနိုင်ပါတယ်။

```bash
$ docker system prune -a -f
$ dokcer image prune -a -f
$ docker container prune -a -f
$ docker network prune -a -f
$ docker volume prune -a -f
```

Reference from [tecadmin](https://tecadmin.net/tutorial/docker/docker-prune-unused-objects/).

