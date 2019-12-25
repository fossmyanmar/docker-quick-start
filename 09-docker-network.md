# Docker Networking

## Docker Networking

Docker မှာ Network တွေကို docker containers နှင့် ဆက်သွယ်ဖို့အတွက် create နဲ့ manage လုပ်ဆောင်ချက်တွေ ကို ထောက်ပံ့ပေးထားပါတယ်။ **docker network command** ကို အသုံးပြုပြီးတော့ Docker network ကို manage လုပ်လို့ရပါတယ်။

**Syntax:**

```text
$ docker network [options]
```

အောက်ပါ Tutorial ကို လေ့လာပြီး Docker network ကို create , list နဲ့ manage စတဲ့ features တွေကို လုပ်ဆောင်လို့ရပါတယ်။

## Docker Networks များ ကို List လုပ်ခြင်း။

`ls` option ကို အသုံးပြုပြီး docker host ပေါ်မှာ ရှိတဲ့ docker network တွေ ကို List လုပ်လို့ရပါတယ်။

```text
$ docker network ls
```

## Docker Network တခု Create လုပ်ခြင်း။

Network အမျိုးအစား အမျိုးမျိုးကို Docker မှ ထောက်ပံ့ပေးထားပါတယ်။ သင့်ရဲ့ system ပေါ်မှာ a bridge Network တခုကို အောက်ပါ command အသုံးပြုပြီး create လို့ရပါတယ်။

**Syntax:**

```text
$ docker network create -d [network_type] [network_name]
```

**Example:**

```text
$ docker network create -d bridge my-bridge-network
```

## Container ကို Network ချိတ်ခြင်း။

Container နာမည် \(သို့မဟုတ်\) Container ID ကို အသုံးပြုပြီး မည်သည့် container ကိုမဆို ရှိပြီးသား docker network နဲ့ ချိတ်ဆက်နိုင်ပါတယ်။ Container တစ်ခုကို Network နဲ့ တစ်ချိန် ချိတ်ဆက်ထားရုံနဲ့ အခြား container များကိုလဲ တူညီတဲ့ Network တခုတည်းပေါ်မှာ ဆက်သွယ်လုပ်ဆောင်လို့ရပါတယ်။

**Syntax:**

```text
  $  docker network connect [network_name] [container_name]
```

**Example:**

```text
  $ docker network connect my-bridge-network centos
```

## Docker Network နှင့် Container ကို disconnect လုပ်ခြင်း။

သင့်အနေနဲ့ Network တခုပေါ်ကနေ container ကို disconnect လုပ်ချင်ရင် အောက်ပါ command ကို အသုံးပြုနိုင်ပါတယ်။

**Syntax:**

```text
$ docker network disconnect [network_name] [container_name]
```

**Example:**

```text
  $ docker network disconnect my-bridge-network centos
```

## Docker Network တခုရဲ့ အချက်အလက် ကိုကြည့်ခြင်း။

Docker Network တခုရဲ့ အသေးစိတ်အချက် ကို ကြည့်ချင်ရင် inspect option ကို အသုံးပြုပြီး ကြည့်လို့ရပါတယ်။

```text
$ docker network inspect my-bridge-network
```

inspect option ကို အသုံးပြုပြီး Docker Network တခုရဲ့ အသေးစိတ် အချက်အလက်ကိုကြည့်မယ် ဆိုရင် အခုလိုမြင်ရမှာ ဖြစ်ပါတယ်။

## Docker Network ကို Remove ခြင်း။

Docker network တွေကို remove လုပ်မယ်ဆိုရင် rm option ကို အသုံးပြုလို့ပါတယ်။

တခုထက်ပိုတဲ့ docker network တွေကို remove လုပ်ချင်ရင် network ID \(သို့မဟုတ်\) network name တွေကို space ခံပြီး အသုံးပြုပြီး remove လုပ်လို့ရပါတယ်။

**Example:**

```text
  $ docker network rm my-bridge-network network2 network3
```

သင့်အနေနဲ့ docker ပေါ်က အသုံးမပြုတော့တဲ့ network အားလုံးကို remove လုပ်ချင်ရင် prune option ကို အသုံးပြုပြီး remove လုပ်လို့ရပါတယ်။

```text
$ docker network prune
```

