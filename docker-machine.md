# Docker Machine

## Working With Docker Machine

Docker Machine သည် Command Line Tool တစ်ခုဖြစ်ပြီး Dockerized Hosts များကို Provisioning and Managing ပြုလုပ်ရန် ဖြစ်သည်။ အရှင်းဆုံးပြောရရင် Virtual Machine များကို Docker Engine နဲ့ Local or Remote System အတွက် Install ပြုလုပ်နိုင်တယ်။ Docker Machine များသည် Virtualbox, Vmware, Digital Ocean နှင့် Amazone စသည့် Platform များပေါ်တွင်လည်း ကောင်းစွာအလုပ်လုပ်နိုင်သည်။

### Install Docker Machine

Docker Machine ကို install ပြုလုပ်ရန် အောက်တွင်ဖော်ပြထားပါသည်။ ပြီးတော့ [https://github.com/docker/machine/releases](https://github.com/docker/machine/releases) တွင်လည်း နောက်ဆုံးထွတ် Docker Machine Version ကို စစ်ဆေးရွေးချယ်နိုင်ပါသည်။

```text
** Please Note: : " https://github.com/docker/machine/releases " 
```

#### For Linux Systems:

```text
$ curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine

$ chmod +x /usr/local/bin/docker-machine
```

စသည့် Command ကို အသုံးပြုပြီး Docker Machine ကို Download ပြုလုပ်ပြီး Install ပြုလုပ်နိုင်သည်။

#### For OSX Systems:

```text
$ curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine

$ chmod +x /usr/local/bin/docker-machine
```

စသည့် Command များကို အသုံးပြုပြီး download and install ပြုလုပ်နိုင်သည်။

#### For Windows Systmes with Git Bash:

Windows 10 နှင့် အထက်တွင်သာ အသုံးပြုရန် အကြံပြုလိုပါသည်။

```text
$ if [[ ! -d "$HOME/bin" ]]; then mkdir -p "$HOME/bin"; fi

$ curl -L https://github.com/docker/machine/releases/download/v0.12.2/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe"

$ chmod +x "$HOME/bin/docker-machine.exe"
```

စသည့် Command များကို အသုံးပြုပြီး download and install ပြုလုပ်နိုင်သည်။

### Docker Machine Supported Drivers:

Docker Machine အတွက် Drivers များကို local and Cloud System များကို Provide လုပ်ပေးပါသည်။

Dockerized hosts များ၏ ဖော်ပြပါ hosting Service များကို Docker Machine တခုတည်းဖြင့် Manage ပြုလုပ်နိုင်ပါသည်။

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

