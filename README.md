## Requisitado pelo professor: Alaelson Jatobá <br /> Disciplina: Infraestrutura de Redes <br /> Data: 01/09/2020 <br /> Turma: 923 <br /> Grupo: 3

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

## Ping para 192.168.23.35, www e srv-vm1-pc2


## Acessando remotamente a VM2 do PC 2

![image](https://user-images.githubusercontent.com/64742095/187787624-16783ef0-55ad-4a57-83af-4b46bc2aaacd.png)

## Ping para 192.168.23.56, violeiro e srv-vm2-pc3-natan

## Acessando remotamente a VM1 do PC 3

## Ping para 192.168.23.55, tim e srv-vm1-pc3-natan

## Acessando remotamente a VM1 do PC 3
 
## Acessando remotamente a VM1 do PC 2 via nome do usuário
 
## Acessando remotamente a VM1 do PC 1 via nome do usuário
  
## Acessando remotamente a VM1 do PC 3 via nome do usuário


