![capa](imap-nfse-capa.png)

# IMAP NFS-e
> Módulo fiscal (Nota Fiscal de Serviço eletrônica).
> **De ColdFusion 11 → .NET 9 / Docker.** Em produção em `sga.imap.org.br`.
> *Uma frente do **[Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md)**.*

---

## O que é

O núcleo fiscal que **emite e gerencia NFS-e**. Rodava em **ColdFusion 11** sobre **Windows Server 2012 R2** (ambos fora de suporte) — ou seja, emitindo nota fiscal sobre um servidor sem manutenção.

## De → Para

| Dimensão | Antes (legado) | Depois (entregue) |
|---|---|---|
| Plataforma | ColdFusion 11 (EOL) | **.NET 9 · open-source** |
| Sistema operacional | Windows Server 2012 R2 (EOL) | **Linux + Docker** |
| Licenciamento | CF + Windows (pago) | **R$ 0 (open-source)** |
| TLS/HTTPS | manual | **Let's Encrypt automático** |
| Gestão de segredos | prática legada | **segredos protegidos** |
| Testes automatizados | nenhum | **49**, com blindagem do XML fiscal |
| Entrega | manual | **CI + deploy conteinerizado** |
| NFS-e Nacional | inexistente | **pronta** (emissão + conciliação) |

## 🏆 Ganhos desta frente

- **🚀 Modernização — NFS-e Nacional pronta antes da obrigatoriedade.** Padrão federal **SNNFSe** completo: montagem, validação, **assinatura digital**, transmissão de DPS, listagem via ADN e **conciliação local × nacional**.
- **💸 Custos — núcleo fiscal sem licença de plataforma.** .NET 9, Docker e Linux open-source; o serviço `imap-nfse` divide o host consolidado com as demais frentes.
- **🧱 Endurecimento — não sobe malconfigurado.** **Validação de configuração na inicialização** + **segredos protegidos**: erro de ambiente vira falha de partida, não incidente fiscal.
- **🛡️ Salvaguarda — o XML fiscal é blindado.** Teste **"golden"** do documento fiscal **bloqueia o deploy** se um byte mudar; **assinatura mTLS com o fisco**; **49 testes verdes** a cada build.
- **🧭 Futuro — adesão nacional como diferencial.** A mesma fundação recebe os módulos restantes — e estar pronto para a NFS-e Nacional **antes** da exigência vira vantagem comercial imediata.

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## 📍 Provas (em produção)

- Produção: **`https://sga.imap.org.br`** com TLS válido.
- **49 testes** verdes a cada build.
- Banco de produção conectado, health-check `ready` = OK.
- **Consolidação confirmada** — compartilha o host Docker com ~14 outros serviços.

## 🧰 Tecnologias

.NET 9 (C#) · Docker · Linux/OCI · Let's Encrypt · CI — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

## 🗺️ Roadmap

1. **Migrar os módulos restantes** do ColdFusion com o mesmo modelo → desligar o Windows Server 2012 R2.
2. **Ativar a NFS-e Nacional** em produção (certificado + adesão).
3. **Auditoria de acessibilidade** formal (rumo a WCAG).
