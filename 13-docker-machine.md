# Docker Machine

## Working With Docker Machine

Docker Machine သည် Command Line Tool တစ်ခုဖြစ်ပြီး Dockerized Hosts များကို Provisioning and Managing ပြုလုပ်ရန် ဖြစ်ပါတယ်။ အရှင်းဆုံးပြောရရင် Virtual Machine များကို Docker Engine နဲ့ Local or Remote System အတွက် Install ပြုလုပ်နိုင်ပါတယ်။ Docker Machine တွေဟာ Virtualbox, Vmware, Digital Ocean နှင့် Amazone AWS စသည့် Platform တွေပေါ်မှာလည်း ကောင်းစွာအလုပ်လုပ်နိုင်ပါတယ်။

### Install Docker Machine

Docker Machine ကို install ပြုလုပ်နိုင်တဲ့နည်းတွေကို အောက်မှာဖော်ပြထားပါတယ်။ ပြီးတော့ [https://github.com/docker/machine/releases](https://github.com/docker/machine/releases) တွင်လည်း နောက်ဆုံးထွက် Docker Machine Version ကို စစ်ဆေးရွေးချယ်နိုင်ပါတယ်။

```text
** Please Note: : " https://github.com/docker/machine/releases " 
```

#### For Linux Systems:

```text
$ curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine

$ chmod +x /usr/local/bin/docker-machine
```

စသည့် Command ကို အသုံးပြုပြီး Docker Machine ကို Download ပြုလုပ်ပြီး Install ပြုလုပ်နိုင်ပါတယ်။

#### For OSX Systems:

```text
$ curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine

$ chmod +x /usr/local/bin/docker-machine
```

စသည့် Command များကို အသုံးပြုပြီး download and install ပြုလုပ်နိုင်ပါတယ်။

#### For Windows Systmes with Git Bash:

Windows 10 နှင့် အထက်တွင်သာ အသုံးပြုရန် အကြံပြုလိုပါတယ်။

```text
$ if [[ ! -d "$HOME/bin" ]]; then mkdir -p "$HOME/bin"; fi

$ curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe"

$ chmod +x "$HOME/bin/docker-machine.exe"
```

စသည့် Command များကို အသုံးပြုပြီး download and install ပြုလုပ်နိုင်တယ်။

### Docker Machine Supported Drivers:

Docker Machine ဟာဆိုရင် အောက်ဖော်ပြပါ services တွေရဲ့ local system တွေအတွက်သာမဟုတ်ပဲ Cloud System တွေအတွက်ကိုပါ Drivers များကို Provide လုပ်ပေးပါတယ်။

အောက်ဖော်ပြပါမည်သည့် hosting Service ကိုမဆို အသုံးပြုပြီး Dockerized hosts များကို launchလုပ်နိုင်ပြီး Docker Machine တစ်ခုတည်းဖြင့် Manage ပြုလုပ်နိုင်ပါတယ်။

* Amazon Web Services
* Microsoft Azure
* Digital Ocean
* Exoscale
* Google Compute Engine
* Generic
* 6Microsoft Hyper-V
* OpenStack
* Rackspace
* IBM Softlayer
* Oracle VirtualBox
* VMware vCloud Air
* VMware Fusion
* VMware vSphere

