# Projeto Final – Administração de Redes de Computadores

**Alunos:** Edvaldo Abreu e Iasmyn Severo  
**Data de entrega:** 02 de dezembro de 2025  
**Repositório GitHub:** https://github.com/Edmurk/ProjetoFinal-Redes-de-Computadores  
**Ambiente utilizado:** EVE-NG Community (VM fornecida pela Redesbrasil) rodando no VMware Workstation  

---

## Objetivo do Trabalho

Implementar uma rede empresarial completa utilizando Linux e Mikrotik, com os seguintes serviços obrigatórios:

1. Servidor DHCP  
2. Servidor DNS  
3. Servidor Web (Apache)  
4. Servidor FTP  
5. Servidor NFS  

---

## Topologia da Rede

![Topologia da Rede](https://github.com/Edmurk/ProjetoFinal-Redes-de-Computadores/blob/main/image.png)

### Tabela de Endereçamento dos Dispositivos (DHCP)

| Nome                  | Sistema Operacional       | IP               | Função Principal                     |
|-----------------------|---------------------------|------------------|--------------------------------------|
| MK01                  | Mikrotik RouterOS         | 192.168.80.1     | Gateway, DHCP Server, NAT, DNS       |
| Linux-Apache          | Ubuntu                    | 192.168.80.253   | Servidor Apache                      |
| Linux-FTP             | Ubuntu                    | 192.168.80.252   | Servidor FTP                         |
| Client-NFS            | Ubuntu                    | 192.168.80.251    | Servidor NFS                         |
| Client-Linux (DHCP)   | Ubuntu                    | 192.168.80.254   | Teste NFS e FTP                      |


---

## Comandos Executados

### Servidor Apache  
```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl enable apache2
```

### Servidor FTP  
```bash
sudo apt update
sudo apt install 

```

### Servidor NFS  
```bash
sudo apt update
sudo apt install 
```
