# bitbucket_server 설치

## Docker 설치

```console
  $ sudo su 
  $ git clone https://github.com/kin3303/bitbucket_server.git
  $ cd bitbucket_server
  $ git checkout master
  $ chmod +x install.sh && ./install.sh
  $ docker swarm init
```

## Bitbucket Server 설치 
 
###  Step 1. 도메인, SSL 설정

1. `traefik.yaml` 을 열어 `Challenge HTTP` 섹션의  `email:`  을 수정 
2. `docker-compose.yaml` 파일을 열어 <YOUR_DOMAIN> 에 Bitbucket 도메인을 입력 
3. `docker-compose.yaml` 파일을 열어 DB 설정을 수정한다.
     - 'POSTGRES_USER=bitbucketdb' 
     - 'POSTGRES_PASSWORD=password'
     - 'POSTGRES_DB=bitbucketdb'

###  Step 2. Bitbucket 배포

```console
  $ docker stack rm bitbucket
  $ docker stack deploy -c docker-compose.yaml bitbucket 
```

### Step 3. Potainer 활성화

- Portainer 는 5분 내에 admin 계정을 생성해야 사용 가능하다. 

```
  Portainer - http://<YOUR_HOST>:9000
```

### Step 4. Traefik 확인

- 도메인에 대한 무료 SSL 인증과 연장을 수행하며 Web Server 로써 Reverse Proxy 역할을 하는 Traefik 이 설치된다.

```
 Traefik  - http://<YOUR_HOST>:8080
```

### Step 5. DB 설정

- https://<YOUR_DOMAIN> 으로 접속하여 Step1 에서 수정한 설정 (DB이름, 사용자, 패스워드)으로 BitBucket 서버와 DB 를 연결한다.
