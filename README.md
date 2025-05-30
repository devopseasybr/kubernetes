<h1 align="center" style="border-bottom: none">
    <img alt="Kubernetes" src="./img/kubernetes.png" width="300" height="200">
</h1>

<center><h1>Kubernetes</h1></center>

<p align="center">Acesse o <a href="https://kubernetes.io/docs/home/" target="_blank">site oficial</a> 
para uma documentação completa, exemplos e guias.</p>

---

Este projeto simplifica a instalação do Kubernetes em servidores on-premise, ideal para ambientes de ```laboratório```, ```testes``` e ```experimentação```.

## Pré-requisitos

 * Providenciar dois servidores virtuais ou locais com as seguintes configurações:

|Sistema Operacional|CPU|Memória| Disco
|:--                |:--: |:--:|:--:  | 
|Ubuntu 24.04.1     |2   |3GB   |40GB 

* Certificar-se de que os dois servidores estão se comunicando na rede.

## Cluster Kubernetes

O cluster será formado por dois servidores: um atuará como **Master** e o outro como **Node**, com a capacidade de ambos executarem Pods. 

Para um entendimento aprofundado do processo de instalação, optei por não fornecer scripts. 

A ideia é que você execute e **compreenda** cada comando passo a passo.

## Procedimento de instalação

Este guia pressupõe que você já tem uma compreensão básica de Kubernetes e seus [componentes](https://kubernetes.io/docs/concepts/overview/components/), bem como experiência com o sistema operacional Linux. Isso garantirá que você possa acompanhar os passos com mais facilidade.  

### Configuração do arquivo /etc/hosts

**Servidores:** Master-Node e Worker-Node

```java
192.168.0.100 master-node.devopseasybr.local master-node
192.168.0.101 worker-node.devopseasybr.local worker-node
```

### Instalação do Docker

**Servidores:** Master-Node e Worker-Node

```java
apt-get update
apt-get install ca-certificates curl
install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
            $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
            tee /etc/apt/sources.list.d/docker.list > /dev/null

apt-get update
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```