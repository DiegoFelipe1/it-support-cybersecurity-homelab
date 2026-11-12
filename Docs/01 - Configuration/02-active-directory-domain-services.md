# Active Directory Domain Services e DNS

## Objetivo

Transformar o servidor `DC01` em um controlador de domínio e criar uma infraestrutura básica de Active Directory para o laboratório.

## Instalação das funções

No Server Manager foram adicionadas as funções:

- Active Directory Domain Services (AD DS)
- DNS Server

Após a instalação, o servidor foi promovido a controlador de domínio.

## Criação da floresta

Foi criada uma nova floresta utilizando o domínio:

`novatech.exemple`

O servidor `DC01` passou a atuar como primeiro Domain Controller do ambiente.

## DNS

Durante a promoção do servidor, o serviço DNS foi instalado e integrado ao Active Directory.

Foram criadas automaticamente zonas como:

- `novatech.exemple`
- `_msdcs.novatech.exemple`

## Validação do domínio

A configuração do domínio foi validada com PowerShell:

```powershell
Get-ADDomain | Select-Object DNSRoot,NetBIOSName,DomainMode
```

Também foi possível validar a floresta:

```powershel
Get-ADForest | Select-Object Name,RootDomain,ForestMode
```

Validação do DNS
As zonas DNS foram consultadas utilizando:

```powershel
Get-DnsServerZone
```

Também foi validada a resolução do próprio controlador de domínio:

```powershel
Resolve-DnsName dc01.novatech.exemple -Server 192.168.122.10
```

Resultado esperado:
dc01.novatech.exemple
192.168.122.10

Serviços do domínio
Foram verificados serviços essenciais como:
- DNS Server
- Netlogon
- Active Directory Domain Services
O controlador de domínio também registrou os registros SRV necessários para serviços como LDAP e Kerberos.
Resultado
Ao final desta etapa, o laboratório possuía:
- Controlador de domínio DC01
- Domínio novatech.exemple
- DNS integrado ao Active Directory
- Resolução interna de nomes funcionando
- Serviços LDAP e Kerberos disponíveis