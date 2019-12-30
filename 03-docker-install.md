# Docker Install

## Docker installation on Ubuntu

**Docker ကို ubuntu OS မှာ install ပြုလုပ်ဖို့ အောက်ပါ command တွေကို တခုချင်း terminal တွင်ရိုက်ထည့်ပါ။**

* ပထမဆုံး လက်ရှိ package များကို update ပြုလုပ်ပါမယ်။

```text
$ sudo apt-get update
```

* ထို့နောက် လိုအပ်တဲ့ package များကို သွင်းပါမယ်။

  ```text
  $ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
  ```

* ထို့နောက် Docker repository ကို add လုပ်ပါမယ်။

  ```text
  $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  ```

  ```text
  $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  ```

* နောက်ဆုံးအဆင့်အနေနဲ့ update ပြုလုပ်ပြီး docker ကို သွင်းနိုင်ပါပြီ။

  ```text
  $ sudo apt-get update
  ```

  ```text
  $ sudo apt-get install docker-ce docker-ce-cli containerd.io
  ```

* Docker service run နေကြောင်းကို သိရှိနိုင်ရန် ယခုကဲ့သို့ ရိုက်ထည့်ပါ။

  ```text
  $ sudo systemctl status docker
  ```

`Active: active` ဖြစ်နေပါက docker service run နေကြောင်း သိရှိနိုင်ပါတယ်။

Docker daemon service နှင့်အတူ docker cli ကိုပါ တပါတည်း ထည့်သွင်းထားတဲ့ အတွက် docker cli ကိုလဲ အသုံးပြုနိုင်မှာဖြစ်ပါတယ်။Docker command များ ကို ယခုလို ကြည့်ရှုနိုင်ပါတယ်။

```text
$ docker
```

```text
Output:


Management Commands:
  builder     Manage builds
  config      Manage Docker configs
  container   Manage containers
  context     Manage contexts
  engine      Manage the docker engine
  image       Manage images
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Commands:

  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  deploy      Deploy a new stack or update an existing stack
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes
```

ဒါပေမယ့် docker ကို ထည့်သွင်းလိုက်ချိန်မှာ root user အနေနဲ့သာ docker နဲ့ သက်ဆိုင်တဲ့ command တွေကို ရိုက်သွင်းနိုင်မှာဖြစ်ပါတယ်။ မိမိက docker နဲ့ command တခုခုကို run မယ်ဆိုရင် sudo command နဲ့သာ အသုံးပြုနိုင်မှာ ဖြစ်ပါတယ်။ ဥပမာ..

```text
  $ sudo docker image ls
```

Docker ကို ထည့်သွင်း ချိန် docker ဆိုတဲ့ linux user group တခုကို docker က create လုပ်သွားမှာဖြစ်ပါတယ်။ တကယ်လို့ မိမိက sudo ကို အမြဲ မထည့်ပေးစေချင်ဘူးဆိုရင် docker group ထဲကို လက်ရှိ user ကို add ပေးလိုက်ခြင်းဖြင့် sudo command ကို အမြဲရိုက်ထည့်ပေးစရာမလိုပဲ အသုံးပြုနိုင်ပါတယ်။

```text
$ sudo usermod -aG docker ${USER}
```

ထို့နောက် docker service ကို restart ချပါ။

```text
$ sudo systemctl restart docker
```

Docker service active ဖြစ်လာပါက docker ကို စတင် အသုံးပြုနိုင်မှာဖြစ်ပါတယ်။

