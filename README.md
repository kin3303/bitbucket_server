# bitbucket_server 설치

## Step 1 > Docker 설치

- Tested with 24GB memory, 8 cores,  Ubuntu 16.04 LTS  

```console
  $ sudo su 
  $ sysctl -w vm.max_map_count=262144
  $ sysctl -w fs.file-max=65536
  $ ulimit -n 65536
  $ ulimit -u 4096
  $ git clone https://github.com/kin3303/DDI_OPENSHIFT.git
  $ cd DDI_OPENSHIFT
  $ git checkout testEnv
  $ cd nexus
  $ chmod +x install.sh && ./install.sh
  $ docker swarm init
```

## Bitbucket Server 설치 
 
###  Step 1. 도메인, SSL 설정

1. `traefik.yaml` 을 열어 `Challenge HTTP` 섹션의  `email:`  을 수정 
2. `docker-compose.yaml` 파일을 열어 `- bitbucket.idtplatteer.com` 에 Bitbucket 도메인을 입력 
