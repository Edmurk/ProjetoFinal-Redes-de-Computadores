# Projeto Final – Administração de Redes de Computadores

**Alunos:** Edvaldo Abreu e Iasmyn Severo  
**Data de entrega:** 02 de dezembro de 2025  
**Repositório GitHub:** https://github.com/Edmurk/ProjetoFinal-Redes-de-Computadores  
**Link para download da VM:** https://drive.google.com/file/d/11RvtmEU6Zgfx2KdX_MB7osqAOsUQY2QK/view?usp=sharing   
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
| Client-NFS            | Ubuntu                    | 192.168.80.251   | Servidor NFS                         |
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
sudo apt install ssh
sudo apt install ssh-server
sudo adduser --shell /bin/bash ftpuser
sudo nano /etc/ssh/sshd_config
  # Restrição para usuários SFTP apenas
  Match User ftpuser
      ForceCommand internal-sftp
      ChrootDirectory /home/ftpuser
      AllowTcpForwarding no
      X11Forwarding no
sudo systemctl restart ssh
```

### Cliente  
```bash
sudo apt update
sftp fptuser@192.168.80.252
password:123
```

### Servidor NFS  
```bash
sudo apt update
sudo apt install nfs-kernel-server -y

cd /home/
sudo mkdir -p /compartilhamento
sudo chown nobody:nogroup /compartilhamento
sudo chmod 777 /home/compartilhamento

sudo nano /etc/exports
  # liberado para toda a rede local
  /home/comparilhamento          192.168.80.0/24(rw,sync,no_subtree_check)
sudo exportfs -ra
sudo systemctl restart nfs-kernel-server

teste para ver as pastas que serão montáveis
showmount -e localhost
```

### Cliente  
```bash
sudo apt update
sudo apt install nfs-common -y
sudo mkdir -p /mnt/compartilhamento
sudo mount 192.168.80.100:/home/compartilhamento /mnt/dados

para testar utilizei o nano
```
