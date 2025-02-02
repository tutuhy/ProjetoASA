# Projeto de ASA

## Integrantes do Grupo
- **José Rodrigo Sousa Padilha** - 20231380017  
- **Arthur de Macedo Muniz** - 20231380021  

---

## Objetivo

Subir um host com Vagrant e realizar as atualizações de forma automatica dos serviços requiridos na atividade usando o Ansible.

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
3. Instalar plugin para manter as VirtualBox Guest Additions atualizadas automaticamente no sistema convidado (guest) ao usar o Vagrant
    ```
    vagrant plugin install vagrant-vbguest
    ```
4. Digite o comando:
    ```
    vagrant up
    ```
