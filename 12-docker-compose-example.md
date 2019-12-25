# Docker Compose Example

### Step 1 – Create Directory Structure <a id="step-1-&#x2013;-create-directory-structure"></a>

ပထမဆံုး အနေျဖင့္ docker compose အမည္ရွိ directory တစ္ခု တည္ေဆာက္ပါမည္။ ထို႔ ေနာက္ web application သိမ္းဆည္းရန္ webapp အမည္ရွိ directory တည္ေဆာက္ပါမည္။ webapp directory ထဲတငြ္ web application ကိုစမ္းရန္ အတကြ္ index.html ကို တည္ေဆာက္ပါမည္။

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>$ mkdir dockercompose &amp;&amp; cd dockercompose</p>
        <p>$ mkdir webapp &amp;&amp; echo &quot;It Works&quot; &gt; webapp/index.html</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>### Step 2 – Create Dockerfile for Webapp <a id="step-2-&#x2013;-create-dockerfile-for-webapp"></a>

ျပီးေနာက္ web application အတကြ္ လုိအပ္ေသာ dockerfile ကို webapp directory ထဲမွာတည္ေဆာက္ပါမည္။  dockerfile သည္ web application အတကြ္ လုိအပ္ေသာ apache web server ပါ၀င္သည့္ customized image တည္ဆာက္ ရန္ျဖစ္ပါသည္။ 

```text
$ vim  webapp/Dockerfile
```

ထို႔ ေနာက္ ေအာက္ ပါ code မ်ားကို ေပါင္းထည့္ပါ။

```text
FROM tecadmin/ubuntu-ssh:16.04

RUN apt-get update \
   && apt-get install -y apache2

COPY index.html /var/www/html/
WORKDIR /var/www/html
CMD ["apachectl", "-D", "FOREGROUND"]
EXPOSE 80
```

### Step 3 – Create Docker Compose File <a id="step-3-&#x2013;-create-docker-compose-file"></a>

ထို႔ ေနာက္ လက္ရိွ directory ထဲတငြ္ docker-compose.yml အမည္ရိွ docker configuration ဖိုင္ တစ္ခုကို တည္ေဆာက္ပါမည္။ ထို configuration ဖိုင္ သည္ အသံုးျပဳမည့္ containers အကုန္လံုးကို ကိုယ္စားျပဳမည္ျဖစ္သည္။

```text
$ vim  docker-compose.yml
```

ထို႔ ေနာက္ ေအာက္ ပါ code မ်ားကို ေပါင္းထည့္ပါ။

version: '3' services: db: image: mysql container\_name: mysql\_db restart: always environment:

* MYSQL\_ROOT\_PASSWORD="secret"

  web:

  image: apache

  build: ./webapp

  depends\_on:

  * db

    container\_name: apache\_web

    restart: always

    ports:

  * "8080:80"

အထက္ပါ ဖိုင္သည္ containers နွစ္ခု အတကြ္ျဖစ္သည္။ ပထမ container သည္ mysql database server အတကြ္ျဖစ္ျပီး ဒုတိယသည္ web server အတကြ္ျဖစ္သည္။ Web container သည္ application မ်ားကို apache server တငြ္ အလုပ္လုပ္ေစမည္ျဖစ္သည္။ webapp directory ကို build directory အျဖစ္ သတ္မွတ္ထားျခင္းျဖစ္သည္။

### Step 4 – Build Webapp Image <a id="step-4-&#x2013;-build-webapp-image"></a>

ေအာက္ပါ command ျဖင့္ webapp directory အတငြ္းရွိ contents မ်ားနွင့္ Dockerfile ကို အသံုးျပဳ၍ apache အမည္ရွိ image တစ္ခုကို တည္ေဆာက္ပါမည္။

```text
$ docker-compose build
```



> ```text
> db uses an image, skipping
> Building web
> Step 1/6 : FROM tecadmin/ubuntu-ssh:16.04
> 16.04: Pulling from tecadmin/ubuntu-ssh
> b3e1c725a85f: Pull complete
> 4daad8bdde31: Pull complete
> 63fe8c0068a8: Pull complete
> 4a70713c436f: Pull complete
> bd842a2105a8: Pull complete
> c41407f48fa7: Pull complete
> 1fcfeb9b5ef4: Pull complete
> 13195a7d2240: Pull complete
> b86be64bbda8: Pull complete
> 8c951fe917dc: Pull complete
> f74bc80103b6: Pull complete
> Digest: sha256:523d6fbc97954e9f77231bf54bfcfbbdd4805349887477fbac4a63dc735d777d
> Status: Downloaded newer image for tecadmin/ubuntu-ssh:16.04
>  ---> bb63b492da01
> Step 2/6 : RUN apt-get update    && apt-get install -y apache2
>  ---> Running in 00be0dd717ce
> [[[Removed long output from here]]]
>  ---> 41c731590234
> Removing intermediate container 00be0dd717ce
> Step 3/6 : COPY index.html /var/www/html/
>  ---> 42f84d4c2243
> Removing intermediate container 945aaee6cbde
> Step 4/6 : WORKDIR /var/www/html
>  ---> 40bebd21e352
> Removing intermediate container e13f5f412906
> Step 5/6 : CMD apachectl -D FOREGROUND
>  ---> Running in ab0db1ef1c6e
>  ---> 587bf2323289
> Removing intermediate container ab0db1ef1c6e
> Step 6/6 : EXPOSE 80
>  ---> Running in 7bcbef52d585
>  ---> 8f03d4135394
> Removing intermediate container 7bcbef52d585
> Successfully built 8f03d4135394
> Successfully tagged apache:latest
> ```

### Step 5 – Launch Docker Containers <a id="step-5-&#x2013;-launch-docker-containers"></a>

docker-compose up ကို အသံုးျပဳ၍ containers မ်ားကို စတင္ေစမည္။ Daemon mode ကို အသံုးျပဳရန္ -d option ကို အသံုးျပဳနိုင္သည္။

```text
$ docker-compose up -d
```

### Step 6 – Update Content in Web Application <a id="step-6-&#x2013;-update-content-in-web-application"></a>

Web application တငြ္ ေျပာင္းလဲမွဳ မ်ားျပဳလုပ္လိုလွွ်င္

```text
$ echo "Welcome to Docker Compose Tutorial" >> webapp/index.html
```

ျပီးလွ်င္ ေအာက္ပါ command မ်ားကို သံုး၍ webapp container ကို ျပန္လည္ တည္ေဆာက္ျပီး စတင္ အလုပ္လုပ္ေစနိုင္ပါသည္။

```text
$ docker-compose build
$ docker-compose up -d
```



 

