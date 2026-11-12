# Configuração do Windows Server - DC01

## Objetivo

Criar um servidor Windows Server para atuar como controlador de domínio do laboratório, fornecendo posteriormente serviços de Active Directory e DNS.

## Ambiente

O servidor foi criado como uma máquina virtual utilizando QEMU/KVM através do virt-manager.

Configuração utilizada:

- Sistema operacional: Windows Server 2025 Evaluation
- Nome da máquina virtual: DC01
- Memória RAM: 3 GB
- vCPUs: 2
- Armazenamento: 50 GB
- Rede: virtual `default` em modo NAT
- Firmware: UEFI

## Configuração do hostname

Após a instalação do Windows Server, o nome do computador foi alterado para:

`DC01`

A alteração foi validada utilizando:

```cmd
hostname
```

Configuração de rede
A rede virtual utilizada pelo laboratório pertence à faixa:
192.168.122.0/24
O servidor foi configurado com endereço IPv4 estático:
- IP: 192.168.122.10
- Máscara: 255.255.255.0
- Gateway: 192.168.122.1
- DNS: 192.168.122.10
O uso de IP estático é importante porque o servidor passará a fornecer serviços essenciais aos clientes do domínio.
Validação
A configuração foi validada utilizando:
ipconfig /all

Também foi testada a comunicação com o gateway:
ping 192.168.122.1

Resultado
O DC01 ficou preparado para receber os serviços de Active Directory Domain Services e DNS.

