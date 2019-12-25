# Working with Dockerfile

Dockerfile ဆိုတာ နာမည်​အတိုင်းပဲ file တစ်​ခုပါပဲ။ 
သူ့ဆီမှာ တိကျတဲ့ instructions ​တွေပါမယ်​ အဲ့ instructions ​တွေနဲ့ ကိုယ်​လိုချင်​တဲ့ customized images ​တွေကို​ build လုပ်​ပါတယ်​
Default အ​နေနဲ့​တော့ နာမည်​ကို Dockerfile လို့ တ​ဝေမသိမ်း​ပေးရပါမယ်​။


## Build Image with Dockerfile
```
$ docker build -t image_name .
```
ဒါက​တော့ ​ရေးပြီးသား dockerfile နဲ့ image build လုပ်​တဲ့ command ပါ။
`-t `ဆိုတာ tag name ကိုကိုယ်​စားပြုပါတယ်​ သူ့အ​နောက်​မှာ image name လိုက်​ပါတယ်​
​သေချာကြည်​့ပါ command အဆုံးမှာ `( . )` ပါပါတယ်​ သူက current working directory မှာ ရှိတဲ့ Dockerfile ကိုယူပြီးသုံးမယ်​လို့ ဆိုလိုတာပါ
အကယ်​၍ ခင်​​ဗျားမှာသာ Dockerfile တစ်​ခုမက ရှိ​နေရင်​ သို့မဟုတ်​ Dockerfile မှာ နာမည်​အစ D ကသာ small letter (d) ဖြစ်​​နေခဲ့မယ်​ဆိုရင်​ error တက်​နိုင်​ပါတယ်​
```
$ docker build -t image_name -f /path/to/Dockerfile 
```
ဒီ command ကလဲ image build တဲ့ command ပါပဲ။
ထူးခြားတာက​တော့ `-f` flag ကိုသုံးထားတာပါ။
Current working directory ထဲကမဟုတ်​ပဲ ခင်​​ဗျားရဲ့ file system ထဲက တစ်​​နေရာရာမှာ ရှိတဲ့ Dockerfile ကို ​ခေါ်သုံးချင်​ရင်​ ဒီလို သုံးရပါမယ်​။


## Create a Dockerfile 

ဒီ​နေရာမှာ အစမ်​း​အ​နေနဲ့ Github ​ပေါ်က sample project ကိုယူသုံးပါ့မယ်​
```
$ git clone https://github.com/tecrahul/dockerfile 
$ cd dockerfile
$ docker build -t apacheimage .
```
အ​ပေါ်က command သုံး​ကြောင်းပြီးရင်​ image တစ်​ခု​ဆောက်​ပြီးပါပြီ
​ဆောက်​ပြီးသား images ​တွေကို docker images ဆိုတဲ့ command နဲ့​ခေါ်ကြည့်နိုင်​ပါတယ်​။

## Launch Container with Image
```
$ docker run -it -p 8080:80 apacheimage
```
ဒီcommand နဲ့ ​ဆောက်​ပြီးသား image ကိုသုံးပြီး container တစ်​ခုတည်​​ဆောက်​ပါတယ်​။
`i `က interactive နဲ့ `t `က tty ကို ကိုယ်​စားပြုပါတယ်​။
`-p `ဆိုတာက​တော့ port သတ်​မှတ်​​ပေးတာပါ၊ ဒီ ဥပမာမှာဆို ကိုယ့် host system ရဲ့ port 8080 နဲ့ container ရဲ့ port 80ကို ချိတ်​​ပေးဖို့ သုံးထားတာကို ​တွေ့ရမှာပါ။
အ​ရှေ့က ကိုယ်​့ host systemရဲ့ port ကြားမှာ full coulmn `( : )` နဲ့ အ​နောက်​က container ရဲ့ port ကို​ရေးရမှာပါ။

---
