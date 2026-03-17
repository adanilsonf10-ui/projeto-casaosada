
# 🚀 Projeto CasaOsada: Engenharia de Servidor RK322x
## De Android TV a Servidor Web com Docker e Seguranca Zero Trust

Este projeto documenta a transformacao de uma TV Box MXQ Pro (RK322x) em um servidor Linux robusto. O foco e a superacao de limites de hardware com otimizacao de software.

---

## 🛠️ Especificacoes do Sistema
* **Hardware:** Rockchip RK322x (Quad-Core).
* **Memoria RAM:** 1GB DDR3 (Otimizada via SWAP).
* **OS:** Armbian Linux (Kernel Estavel).
* **Orquestracao:** Docker Engine e CasaOS.

---

## 🏗️ Implementacao Tecnica

### FASE 1: Kernel e OS
- Limpeza da memoria eMMC via Multitool (Wipe).
- Instalacao do Armbian para controle total do hardware.
- Hardening inicial para economia de recursos.

### FASE 2: Virtualizacao e Microservicos
- **Docker:** Isolamento de aplicacoes em containers.
- **CasaOS:** Painel de gestao de ativos e saude do sistema.

### FASE 3: Conectividade Global (Web)
- **Tailscale Funnel:** Tunel reverso para acesso mundial via HTTPS.
- **Diferencial:** Conexao segura em qualquer rede (4G/5G) sem abrir portas no roteador.

---

## 🛡️ Arquitetura de Seguranca Zero Trust
1. **Firewall Stealth:** Roteador com portas fechadas e invisivel para hackers.
2. **Criptografia TLS/SSL:** Trafego protegido ponta-a-ponta.
3. **Privacidade:** O IP real da residencia nunca e revelado.

**Desenvolvido por Adanilson - Analista e Desenvolvedor de Sistemas**
