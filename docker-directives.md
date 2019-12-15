# Dockerfile Directives

## What are Dockerfile Directives

အ​ရှေ့မှာ Dockerfile ကိုသုံးပြီး image ​ဆောက်​ အဲ့ image ကိုသုံးပြီး​တော့ container ​တွေ ​ဆောက်​တာကို မြင်​ခဲ့ရပြီးပါပြီ။

အခု​ပြောမှာက​တော့ အဲ့ Dockerfile ကို ဘယ်​လို​ရေးမလဲဆိုတာပါ။

Dockerfile ကို Docker directive ​တွေနဲ့​ရေးရတာပါ။

### FROM

ဒီ FROM ဆိုတဲ့ directive ကို base image ယူသုံးဖို့အတွက်​ သုံးတာပါ။ ဥပမာ ခင်​​ဗျားက ubuntu command ​တွေ သုံးလို့ရမဲ့ container တစ်​လုံးလိုချင်​တာဆိုရင်​ `FROM ubuntu` ဆိုပြီးသုံးရမှာပါ။

Default အ​နေနဲ့ဆို docker store မှာရှိတဲ့ ubuntu version ​တွေထဲကမှ latest version ကို ယူသုံးသွားမှာပါ အဲ့လိုမှမဟုတ်​ဘူး latest လိုချင်​တာမဟုတ်​ဘူး ကိုယ်​လိုချင်​တာ သက်​သက်​ဆို အခုလို​ရေးလို့ရပါတယ်​ `FROM tecadmin/ubuntu-ssh:16.04`

### LABEL

ဒါက​တော့ နာမည်​အတိုင်​းပဲ label တပ်​တာပါ။ `Maintainer addres​s,vendor name,image version,release date` အစရှိသဖြင့်​ပေါ့။ ဥပမာ

```text
LABEL maintainer="rahul@tecadmin.net"
LABEL vendor="TecAdmin"
LABEL com.example.version="0.01"
```

လို့ ရိုက်​လိုက်​ရုံပါပဲ။ အကြံပြု လိုတာက​တော့ တစ်​ line ထဲကို space ခံ single line ခံပြီး ​ရေးတာကိုပါ။ Image build တဲ့အချိန်​မှာ စာ​ကြောင်းတစ်​​ကြောင်းကို layer တစ်​ခု ​ဆောက်​တာပါ Layer နည်း​လေ မြန်​​လေပါပဲ။

```text
LABEL maintainer="rahul@tecadmin.net" vendor="TecAdmin" \
com.example.version="0.01"
```

### RUN

RUN ကို​တော့ လိုအပ်​တဲ့ command​တွေ run ဖို့သုံးပါတယ်။ ဥပမာ လိုအပ်တဲ့​package​တွေ သွင်းဖို့လိုတဲ့အခါမျိုး​ပေါ့။

```text
RUN apt-get update 
RUN apt-get install -y apache2 automake build-essential curl ​​
```

ဒီ​နေရာမှာလဲ အ​ပေါ်ကလို တစ်​​ကြောင်းထဲဖြစ်​​အောင်​ ​ရေးသင့်ပါတယ်​။ Layer နည်း​လေ​ကောင်း​လေပါ။

```text
RUN apt-get update && apt-get install -y \
automake \
build-essential \
curl
```

### COPY

ဒါကို​တော့ ကိုယ့်စက်​ထဲမှာရှိတဲ့ files ​တွေ directories ​တွေကို ​ဆောက်​မယ့် image ​ပေါ်copy ကူးချင်​ရင်​ သုံးပါတယ်။​

```text
COPY html/* /var/www/html/
COPY *.conf /etc/apache2/sites-available/
```

ပထမ command ရိုက်​လိုက်​ရင်​ host ရဲ့ html directory ​အောက်​က file အကုန်​ကို image ရဲ့ /var/www/html/ ​အောက်​ကို copy ကူသွားမှာပါ။

ဒုတိယ command က​တော့ host ရဲ့ .conf extension file အားလုံးကို image ရဲ့ /etc/apache2/sites-available/ ​အောက်​ကို​ပေါ့။

### WORKDIR

ဒိ directive ကို​တော့ dockerfile ရဲ့အခြား​သော directives ​တွေဖြစ်​တဲ့ `RUN,CMD,ENTRYPOINT,COPY,ADD` ​တွေရဲ့ working directory သတ်​မှတ်​​ပေးဖို့သုံးပါတယ်​

```text
WORKDIR /opt
```

### CMD

CMD directive ကို​တော့ image မှာပါတဲ့ service,software ​တွေကို container launch လုပ်​​တာနဲ့ run ဖို့သုံးပါတယ်။​ သူ့ရဲ့ syntax က​တော့

```text
CMD ["executable","param1","param2"]
CMD ["executable","param1","param2"]
```

အကယ်​၍ခင်​​ဗျားက apache service ကို runချင်​တယ်​ဆိုပါ​တော့

```text
CMD ["apachectl", "-D", "FOREGROUND" ]
```

### EXPOSE

ဒါက container ရဲ့ port ကိုညွှန်းဆိုမဲ့ directive ပါ။ အ​ပေါ်မှာ​တွေခဲ့တဲ့ docker run -it -p နဲ့ port ချိတ်​တာမှာ ဒီက ညွှန်းဆိုထားတဲ့ port ​တွေနဲ့ ချိတ်​​ပေးရပါမယ်​။

```text
EXPOSE 80
EXPOSE 443
```

### ENV

ENV directive ကို​တော့ environment variable သတ်​မှတ်​​ပေးချင်​ရင်​ သုံးတာပါ

```text
ENV PATH=$PATH:/usr/local/psgql/bin/ \
    PG_MAJOR=9.6.0
```

### VOLUME

​နောက်​ဆုံး အ​နေနဲ့​တော့ VOLUME directive ပါ။ သူ့ကို​တော့ mount point create ဖို့ သုံးပါတယ်​။ သိထားဖို့က သူဟာ externally mounted volumes ပဲဖြစ်​ပါတယ်​။

```text
VOLUME ["/data"]
```

