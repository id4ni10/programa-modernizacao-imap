![capa](diario-og.png)

# Diário Oficial — Plataforma Digital
> A face **pública** do Diário Oficial: consultar, ler e ouvir os atos oficiais.
> **De um repositório de PDFs → plataforma digital multi-tenant.** Em produção.
> *Uma frente do **[Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md)**.*

---

## O que é

Transformamos o Diário Oficial de um **repositório de PDFs** numa **plataforma digital moderna, acessível e inteligente** — a mesma base de código atende **centenas de portais municipais**, cada um com sua identidade visual, sem retrabalho.

## De → Para

| Antes | Depois |
|---|---|
| Repositório de PDFs | **Plataforma digital de serviços** |
| Visual datado, igual para todos | **Identidade adaptativa por cidade** |
| Só leitura | **Ouvir por IA + buscar por voz** |
| Acessibilidade limitada | **Fonte, contraste, leitor de tela (LBI/LAI)** |
| Implantação manual | **IaC (Terraform) + entrega contínua** |

## 🏆 Ganhos desta frente

- **🚀 Modernização — uma base, +470 domínios.** Cada cidade assume **automaticamente sua identidade visual** (CSS `color-mix`) — **sem build por cidade, sem retrabalho**.
- **💸 Custos — um deploy atende centenas de portais.** Infraestrutura descrita em **código (Terraform)**: o ambiente inteiro se recria em minutos, sem projeto por município.
- **🧱 Endurecimento — auditável por construção.** Cabeçalhos de segurança, **TLS automático** e IaC — nada de servidor "artesanal" que ninguém sabe reproduzir.
- **🛡️ Salvaguarda — dever legal cumprido.** Controles de fonte, **alto contraste**, HTML semântico e ARIA (leitores de tela) — aderência à **LBI** e à **LAI** — mais **dados abertos** (XML/JSON/CSV) para prestação de contas.
- **🧭 Futuro — o Diário que fala.** **Resumo por IA (TTS)** e **busca por voz**: o cidadão **ouve** o Diário e **pesquisa falando** — diferencial que nenhum repositório de PDFs entregaria; transparência sazonal (Festejos Juninos) pronta para replicar.

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## 📍 Provas (em produção)

- **+470 domínios** publicados numa única plataforma multi-tenant.
- **+500 municípios** atendidos · **+20 anos** de experiência.
- **100% aderente à LAI** · IA + voz nativas.

## 🧰 Tecnologias

Stack web moderna (CSS `color-mix`) · Web Speech API · Terraform · Docker · Linux/OCI · Let's Encrypt — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

## 🗺️ Roadmap

Ampliar recursos de acessibilidade e dados abertos; consolidar a identidade adaptativa e a leitura por voz em toda a base de municípios.
