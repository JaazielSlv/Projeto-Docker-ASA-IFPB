# Projeto: Infraestrutura como Código com Vagrant, Ansible e Docker

![Vagrant](https://img.shields.io/badge/Vagrant-2.4.1-1868F2?style=for-the-badge&logo=vagrant)
![Ansible](https://img.shields.io/badge/Ansible-7.7-EE0000?style=for-the-badge&logo=ansible)
![Docker](https://img.shields.io/badge/Docker-24.0-2496ED?style=for-the-badge&logo=docker)

Projeto acadêmico para a disciplina de **Administração de Sistemas Abertos**, focado na automação completa do provisionamento e configuração de uma infraestrutura web para uma aplicação WordPress, utilizando práticas de Infraestrutura como Código (IaC).

## 📌 Sobre o Projeto

O objetivo deste projeto é demonstrar o uso integrado de ferramentas de automação para construir um ambiente de servidor completo a partir do zero, com um único comando. O fluxo segue três etapas principais:

1.  **Provisionamento:** O `Vagrant` cria e configura uma máquina virtual Debian.
2.  **Configuração:** O `Ansible` é executado para instalar o Docker e orquestrar os containers definidos no `docker-compose.yml`.
3.  **Implantação:** O `Docker Compose` é utilizado para implantar a aplicação WordPress em um ambiente multi-container.

## 🏗️ Arquitetura da Aplicação

A infraestrutura da aplicação é composta por três containers Docker que se comunicam através de uma rede privada, com os dados persistidos em volumes nomeados. Apenas o proxy é exposto para a máquina host.

-   **`webproxy`**: Um container Nginx personalizado atuando como um proxy reverso e Load Balancer de Camada 4. Ele recebe as requisições na porta `8080` e as encaminha para o container do WordPress.
-   **`webserver`**: Um container com a imagem oficial do WordPress, contendo a aplicação PHP e o servidor web Apache.
-   **`database`**: Um container com a imagem oficial do MySQL, servindo como banco de dados para o WordPress.

## 🛠️ Tecnologias Utilizadas

- **Virtualização e Provisionamento:**
  - Vagrant
  - VirtualBox
- **Gerenciamento de Configuração:**
  - Ansible
- **Conteinerização:**
  - Docker
  - Docker Compose
- **Aplicação:**
  - WordPress
  - Nginx
  - MySQL

## 🚀 Como Executar

### Pré-requisitos

Antes de começar, garanta que você tenha os seguintes softwares instalados:
-   VirtualBox
-   Vagrant

### Passo a Passo

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/JaazielSlv/Projeto-Docker-IFPB.git
    ```

2.  **Suba a infraestrutura:**
    Execute o comando que automatiza todo o processo:
    ```bash
    vagrant up
    ```
    *Este processo pode levar vários minutos na primeira execução, pois ele irá baixar a imagem da VM e instalar todos os pacotes.*

3.  **Acesse a aplicação:**
    Após o comando `vagrant up` ser concluído com sucesso, abra seu navegador e acesse a URL:
    [http://192.168.56.155:8080](http://192.168.56.155:8080)

    Você será recebido com a tela de configuração inicial do WordPress.

4.  **Para desligar e limpar o ambiente:**
    Para remover a máquina virtual e liberar os recursos do seu computador, execute:
    ```bash
    vagrant destroy -f
    ```

## 📂 Estrutura dos Arquivos

O projeto é composto por três arquivos principais de configuração, conforme especificado nos entregáveis:

-   `Vagrantfile`: Define e configura a máquina virtual, incluindo suas especificações de hardware, rede e qual provisionador (Ansible) usar.
-   `playbook_ansible.yml`: Contém o roteiro ("playbook") que o Ansible executa para instalar o Docker, copiar arquivos e iniciar os serviços do Docker Compose na VM.
-   `docker-compose.yml`: Descreve o ambiente multi-container da aplicação, definindo os serviços, redes, volumes e portas a serem utilizadas pelo Docker.
-   `nginx-proxy/`: Pasta contendo o `Dockerfile` e `nginx.conf` para a criação da imagem personalizada do Nginx.

## 💻 Desenvolvedores

- Jaaziel Silva
- Lucas Jaasiel

## 🎓 Contexto Acadêmico

Este trabalho foi desenvolvido para a disciplina de **Administração de Sistemas Abertos** do curso de Redes de Computadores do **Instituto Federal da Paraíba (IFPB) - Campus João Pessoa**.

-   **Professor:** Leonidas Lima
-   **Período:** 2025.1
