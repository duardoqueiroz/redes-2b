## Professor: Alaelson Jatobá 
## Disciplina: Infraestrutura e Serviço de Redes
## Data: 08/09/2020 
## Turma: 923 
## Grupo: 4

> ### Integrantes
* Nome: Eduardo Lúcio de Queiroz
* Nome: Guilherme de Jesus Vieira
* Nome: Natan Ryan Mota Ferreira
* Nome: Pedro Daniel da Silva

> ## Objetivos do projeto:
* Colocar em prática o que foi ensinado nas aulas de Infraestrutura e Serviços de Rede
* Criar um tutorial resumido ensinando a fazer a conexão entre VM's de PC's diferentes 
* Testar os conhecimentos adquiridos em aulas


# Definições de endereços IPs da Rede e Nomes de Hosts:

```
----------------------------------------------------------------------------------------------------------------------------
|  DESCRICAO  |  IP                  |   hostname                  |          FQDN                      |     aliase       |
----------------------------------------------------------------------------------------------------------------------------
| VM1-PC1     | 192.168.23.51        |   srv-vm1-pc1-guilherme     | guilherme1.grupo4-923.ifalara.net  |       vpn        |
| VM2-PC1     | 192.168.23.52        |   srv-vm2-pc1-guilherme     | guilherme2.grupo4-923.ifalara.net  |       banana     |
| VM1-PC2     | 192.168.23.53        |   srv-vm1-pc2-pedro         | pedro1.grupo4-923.ifalara.net      |       mamute     |
| VM2-PC2     | 192.168.23.54        |   srv-vm2-pc2-pedro         | pedro2.grupo4-923.ifalara.net      |       tigre      |
| VM1-PC3     | 192.168.23.55        |   srv-vm1-pc3-natan         | natan1.grupo4-923.ifalara.net      |       tim        |
| VM2-PC3     | 192.168.23.56        |   srv-vm2-pc3-natan         | natan2.grupo4-923.ifalara.net      |       violeiro   |
| VM1-PC4     | 192.168.23.57        |   srv-vm1-pc4-eduardo       | eduardo1.grupo4-923.ifalara.net    |       fofo       |
| VM2-PC4     | 192.168.23.58        |   srv-vm2-pc4-eduardo       | eduardo2.grupo4-923.ifalara.net    |       codigo     |
----------------------------------------------------------------------------------------------------------------------------
```

# Modelo de rede criada

![DiagramaRede](https://user-images.githubusercontent.com/64742095/187998980-f5d946bc-e7c4-4514-8161-211bffa7e621.png)

## Topologia Física 
### Estrela
Computadores ligados de forma linear. O final do barramento é onde se localiza o terminal responsável por controlar o fluxo de dados da rede.

## Requisitos de Hardware
### Hardware utilizado nas VM's
* Núcleos lógico de processamento: 1
* RAM: 512MB
* Espaço em disco: 10GB dinamicamente alocados

## Configurando os ambientes

### Baixando o arquivo .ova da máquina virtual com o sistema operacional 

```
scp aluno@192.168.101.55:~/Public/iso-images/ubuntu-server-mini.ova
```

### Antes de iniciar a máquina virtual, baixe o Extension Pack
```
sudo apt install virtualbox-ext-pack
```

# Na VM:

## Fazendo o login
User: administrador <br />
Senha: adminifal

## Definindo o nome da máquina 1
```
sudo hostnamectl set-hostname srv-vm1-pc1-guilherme
```

## Instalando o SSH
```
systemctl status ssh
sudo apt-get install openssh-server
systemctl status ssh
```

## Verificando se a conexão tcp nas portas 22 está como LISTENING
```
netstat -an | grep LISTEN
```
## Configuração do Firewall
Permitindo conexões remotas via SSH
```
sudo ufw status
sudo ufw allow ssh
sudo ufw status
```
## Ativando o Firewall
```
sudo ufw enable
```

## Configurando a interface de rede

![image](https://user-images.githubusercontent.com/83377894/189210609-b69c016d-88a8-41a4-8759-7efc0f528371.png)

## Acessando a VM remotamente

```
ssh <usuário>@<ipDoServidorRemoto>
```
Exemplo

```
ssh administrador@192.168.23.55 #endereço da VM1 do PC3
```

## Configurando rede de hospedeiros para a cominucação entre o Host

![image](https://user-images.githubusercontent.com/83377894/189210255-d7a43852-33f3-4ef8-baef-c336c0c0a157.png)

## Configurando o servidor DHCP no adaptador

![image](https://user-images.githubusercontent.com/83377894/189210719-631d6de9-faee-4cc0-b74a-7f90d2a75d81.png)

## Adicionando o adaptador Host-Only em uma VM

## Ativando o dhcp4 para o adaptador 2
![image](https://user-images.githubusercontent.com/83377894/189211474-f0d82950-e768-44db-a8b2-373033ffdadb.png)

## Acessando a VM remotamente

no terminal do computador
```
ssh administrador@192.168.56.101
```

# Testes/Validações

## Ping para 192.168.23.55, tim e srv-vm1-pc3-natan
![image](https://user-images.githubusercontent.com/83377894/189214975-d44a1ac1-dfda-403a-a732-8b50b30dac67.png)
![image](https://user-images.githubusercontent.com/83377894/189217369-90b34bb6-0b52-4b74-b673-3fcfa9bd977b.png)
![image](https://user-images.githubusercontent.com/83377894/189215329-c5e17001-6b6a-424a-b90a-4bbeab3ff763.png)

## Acessando remotamente a VM1 do PC 3
![image](https://user-images.githubusercontent.com/83377894/189215848-9f57db30-21dd-4593-83fa-4ec3984d4864.png)

## Ping para 192.168.23.53, mamute e srv-vm1-pc2-pedro  
![image](https://user-images.githubusercontent.com/83377894/189216544-024fd314-ac26-492d-9576-e0a34e892693.png)
![image](https://user-images.githubusercontent.com/83377894/189216649-b2d87a1f-d96d-4a0f-8024-077f7b8f136a.png)
![image](https://user-images.githubusercontent.com/83377894/189216742-d13c3440-85c1-467d-a2fb-2eaa289f3154.png)

## Acessando remotamente a VM1 do PC 2
![image](https://user-images.githubusercontent.com/83377894/189217514-73bc54e5-574f-47c4-a594-c84b38e8eea2.png)
    
