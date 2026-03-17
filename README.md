# 🚀 Projeto CasaOsada: Edge Computing Hub (RK322x)
## Da Reciclagem de Hardware ao Servidor Profissional (Mobile, IoT & IA)

Este projeto documenta a jornada técnica de transformação de uma TV Box baseada no chip **Rockchip RK322x** em um servidor Linux robusto. Uma prova de conceito de que hardware acessível pode rodar infraestruturas modernas com **Segurança Zero Trust**.

---

## 🛠️ Especificações de Hardware (Low-Level)
O "coração" do projeto é o SOC (System on a Chip) **Rockchip RK3229/RK3228a**:
- **CPU:** Quad-Core ARM Cortex-A7 (ARMv7).
- **RAM:** 1GB DDR3 (Otimizada via ZRAM e Swap no sistema).
- **Storage:** eMMC Interna (Wipe total para remoção do Android Bloatware).
- **Arquitetura:** 32-bit com suporte a instruções NEON (essencial para acelerar IA leve).

---

## 🏗️ Metodologia de Transformação

### 1. Do Android ao Armbian (O Nascimento)
O primeiro passo foi o "Unbricking" e a remoção das limitações do fabricante:
- **Ferramenta:** Multitool (via MicroSD).
- **Processo:** Limpeza (Wipe) das partições original para instalar o **Armbian (Debian-Based)** diretamente na eMMC.
- **Vantagem:** Liberamos 100% dos recursos do hardware para o kernel Linux.

### 2. Virtualização e HTTPS Global
- **CasaOS & Docker:** Camada de abstração para rodar microserviços isolados.
- **Tailscale Funnel (HTTPS):** Túnel reverso que gera certificados **SSL/TLS** automáticos. 
- **Zero Trust:** Acesso mundial sem abrir portas no roteador (Sem Port Forwarding), mantendo o IP real oculto e seguro.

---

## 🔮 Roadmap: O Próximo Nível (Em Desenvolvimento)
O projeto está em constante evolução. O próximo grande passo é a **Migração para SSD Externo**:
- **Boot Direto:** Configuração do sistema para realizar o boot pela eMMC mas rodar todo o sistema operacional e banco de dados no SSD via USB.
- **Performance:** Fim do gargalo de escrita da eMMC, permitindo modelos de **IA (TinyML)** e **Media Centers (Jellyfin)** mais pesados.

---

## 🧠 Engenharia com Suporte de IA
Este projeto utilizou o **Gemini (IA da Google)** como ferramenta de suporte e co-piloto de desenvolvimento. A IA auxiliou na:
- Otimização de scripts de automação.
- Pesquisa de compatibilidade de Kernel para o chip RK322x.
- Estruturação de protocolos de rede e segurança.

---

## 🛠️ Mão na Massa: Comandos Úteis

### 🔔 Script de Alerta de Acesso (Telegram)
Para monitorar quem entra no seu servidor em tempo real:
```bash
# Salve como alerta.sh e execute em segundo plano
tail -fn0 /var/log/auth.log | while read LINE; do
   if echo "$LINE" | grep -q "Accepted"; then
      msg="🚨 ACESSO DETECTADO: Login realizado no servidor CasaOsada!"
      curl -s -X POST "[https://api.telegram.org/botSEU_TOKEN/sendMessage](https://api.telegram.org/botSEU_TOKEN/sendMessage)" -d chat_id="SEU_ID" -d text="$msg"
   fi
done
