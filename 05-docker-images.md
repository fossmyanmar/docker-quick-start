# Docker Images

## Docker Images

Docker image ဆိုတာကတော့ container တစ်ခုမှာ လိုချင်တဲ့ application တွေ ကိုအသုံးပြုလို့ရအောင်ပြုလုပ်ထားတဲ့ file တစ်ခုပါပဲ။ Docker image တွေဟာ ပြုလုပ်ပြီးတဲ့အချိန်ကစပြီး ဖျက်လိုက်တဲ့အချိန်အထိ အပြောင်းအလဲမရှိနိုင်ပါဘူး။ ထပ်ပြီးပြင်ဆင်လို့လည်းမရနိုင်ပါဘူး။ ပြီးတော့ image တွေဟာ တစ်ခြားသူတွေနဲ့လည်း မျှဝေအသုံးပြုနိုင်ပါသေးတယ်။ ဆိုလိုတာကတော့ တစ်ယောက်ပြုလုပ်ထားတဲ့ image ကိုသုံးပြီး နောက်တစ်ယောက်က ထပ်တူကျတဲ့ container တစ်ခုကို အသုံးပြုနိုင်တာမျိုးပါ။

အောက်မှာတော့ docker images တွေကိုအသုံးပြုဖို့အတွက် အခြေခံကျတဲ့ command တွေကို အကျဥ်းဖော်ပြပေးထားပါတယ်။

## List Docker Images

docker images ဆိုတဲ့ command နဲ့ ကိုယ့်စနစ်ထဲက အသုံးပြုလို့ရတဲ့ image တွေကိုစစ်ကြည့်လို့ရနိုင်ပါတယ်။

```text
$ docker images
```

![](.gitbook/assets/1_ls.png)

## Search Docker Images

docker search ဆိုတဲ့ command ကတော့ [docker hub](https://hub.docker.com/) ကနေ လိုချင်တဲ့ image ကိုရှာတဲ့အခါသုံးပါတယ်။ ဥပမာ WordPress အတွက် images တွေကိုရှာမယ်ဆိုရင် -

```text
$ docker search wordpress
```

![](.gitbook/assets/2_search-large-resolution.png)

## Download Docker Images

လိုချင်တဲ့ image ကိုရှာတွေ့ပြီဆိုရင်တော့ docker pull ဆိုတဲ့ command နဲ့ ကိုယ့်စက်ထဲကို download ဆွဲနိုင်ပါတယ်။ ဥပမာ Docker hub ကနေ WordPress အတွက်နောက်ဆုံးversion ဖြစ်တဲ့image ကို download ချမယ်ဆိုရင်

```text
$ docker pull wordpress
```

![](.gitbook/assets/3_pull_wordpress.png)

## Delete Docker Images

မလိုအပ်တော့တဲ့ image တွေကို ဖျက်ပစ်ဖို့အတွက်ကတော့ docker rmi ဆိုတဲ့ command ကိုသုံးပါတယ်။ ဥပမာ -

```text
 $ docker rmi wordpress
```

![](.gitbook/assets/4_rmi.png)

