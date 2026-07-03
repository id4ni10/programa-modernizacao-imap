![capa](../assets/sections/siej.png)

# SIEJ — Sistema Inteligente de Editoração de Jornais
> Diagramação e gestão de publicações oficiais (DOU, Correio, A Tarde).
> **De ColdFusion 11 (~20 anos) → Python (FastAPI) + React/TypeScript + Docker.** Em produção.
> *Uma frente do **[Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md)**.*

---

## O que é

Sistema **central com ~20 anos de legado**, que diagrama e gere publicações oficiais e trata **dados de cidadãos**. Rodava sobre **duas tecnologias fora de suporte** (ColdFusion 11 + Windows Server 2012 R2) — por isso foi uma das **primeiras frentes modernizadas**.

## De → Para

| Dimensão | Antes (CF11 / WS2012R2) | Depois (FastAPI / React / Docker) |
|---|---|---|
| Frontend | telas antigas | **React + TypeScript + Vite** |
| Backend | ColdFusion 11 | **Python + FastAPI + SQLAlchemy** |
| Banco | SQL Server | **o mesmo SQL Server** (nada descartado) |
| Sistema operacional | Windows Server 2012 R2 | **Linux + Docker** |
| Licenciamento | Adobe CF + Windows | **R$ 0 (open-source)** |
| Testes | inexistentes | **52 (frontend) + suíte no backend**, bloqueiam o deploy |
| Autenticação | legada | **JWT (cookie httpOnly)**, preservando o cartão de acesso |

## 🏆 Ganhos desta frente

- **🚀 Modernização — a ferramenta que o operador pediu.** Editor **WYSIWYG** e **configuração editável em tela** (formatos e margens por veículo — antes fixos no código): o operador ajusta sozinho, sem chamar desenvolvedor.
- **💸 Custos — a fundação que barateia os próximos.** A base (FastAPI · React · Docker · CI · auth IMAP) é **reutilizável** — SGF e SGC **já nascem sobre ela**, mais rápido e mais barato.
- **🧱 Endurecimento — deploy que se defende.** **JWT em cookie httpOnly** preservando o cartão de acesso; **52 testes no front + suíte no back** que **bloqueiam o deploy** se algo quebra.
- **🛡️ Salvaguarda — LGPD ativa, não passiva.** **Detecção automática de irregularidades (CPF/RG)** com **registro permanente**; Financeiro com **paridade verificada** contra o legado (SCP).
- **🧭 Futuro — o piloto do método.** **~20 anos** de sistema renovados **módulo a módulo, lendo o mesmo banco, com rollback** — o roteiro que agora renova o ERP interno.

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## 📍 Provas (em produção)

- Aplicação **no ar**, conectada ao **banco de produção**.
- Fluxo de **diagramação** (DOU, Correio, A Tarde) funcionando.
- **Financeiro** com paridade verificada contra o SCP legado.
- **Detecção de irregularidades (LGPD)** com registro permanente.
- Pipeline com **testes automáticos + deploy com health check**.

## 🧰 Tecnologias

Python · FastAPI · SQLAlchemy · React · TypeScript · Vite · Docker · Linux/OCI — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

## 🗺️ Roadmap

Seguir a migração **incremental**, priorizando os módulos de **maior risco** e **maior custo de manutenção** — até **aposentar ColdFusion 11 + Windows Server 2012 R2**.
