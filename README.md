# Projeto de Administração de Sistemas Abertos

## Integrantes do Grupo
- **José Rodrigo Sousa Padilha** - 20231380017  
- **Arthur de Macedo Muniz** - 20231380021  
- **Professor:** Pedro Filho 

---

## Introdução

Este projeto tem como objetivo principal automatizar tarefas de administração de sistemas utilizando **Vagrant** para provisionamento de servidores virtuais e **Ansible** para configuração e gerenciamento. As principais tarefas incluem:

- Configuração do sistema operacional e pacotes;
- Gerenciamento de usuários, grupos e permissões;
- Configuração de SSH e autenticação por chaves públicas;
- Criação de volumes lógicos com LVM;
- Configuração de NFS para compartilhamento de arquivos;
- Implementação de um sistema de monitoramento de acessos.

---

## Objetivo

Automatizar a configuração de um servidor Linux utilizando Infraestrutura como Código (IaC), permitindo uma implantação padronizada e eficiente.

---

## Funcionalidades Implementadas

### 1. **Provisionamento com Vagrant**
- Criação de uma VM utilizando VirtualBox com 3 discos adicionais e configuração de rede.

### 2. **Automatização com Ansible**
#### Atualização do Sistema
- Atualização completa do sistema e remoção de pacotes obsoletos.

#### Configuração de Hostname
- Alteração automática do hostname conforme o padrão definido.

#### Gestão de Usuários e Grupos
- Criação de usuários e grupos.
- Configuração de permissões e inclusão no grupo `sudo`.

#### Configuração de SSH
- Permitir apenas autenticação por chaves públicas.
- Bloqueio de acesso para o usuário root via SSH.
- Restringir acesso a membros do grupo `acesso_ssh`.

#### Configuração de LVM
- Criação de **Volume Group** (VG) e **Logical Volume** (LV) com os discos adicionais.
- Montagem do LV no diretório `/dados` configurada no arquivo `/etc/fstab`.

#### Configuração de NFS
- Configuração do servidor NFS para compartilhamento seguro do diretório `/dados/nfs`.
- Permissão de escrita somente para o usuário `nfs-ifpb`.

#### Log de Acessos
- Registro de acessos SSH no arquivo `/dados/nfs/acessos`, incluindo data, login, terminal e IP remoto.
- Script de monitoramento configurado para execução em cada login.

---
## Requisitos

- Vagrant
- Ansible
- Virtual Box
- Sistema Operacional baseado em Unix

## Como Executar

1. Clone este repositório e acesse o diretório do projeto.
2. Instale os requerimentos:
   ```bash
   ansible-galaxy install -r requirements.yml
   ```
3. Digite o comando:
    ```
    vagrant up
