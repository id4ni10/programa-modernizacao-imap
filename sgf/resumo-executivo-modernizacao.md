![capa](imap-sgf-capa.png)

# IMAP SGF — Gestão Financeira
> O núcleo **financeiro** do ERP interno: vendas, pagamentos, boletos, faturas, depósitos, remessas bancárias e comissões.
> **De ColdFusion + Windows Server → Python/FastAPI + Astro/Vite + Docker.**
> **Estado: em andamento — a renovação do ERP interno já começou**, sobre a fundação provada.
> *Uma frente do **[Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md)**.*

---

## O que é

O **SGF (Sistema de Gestão Financeira)** é a metade financeira do ERP que sustenta o dia a dia do Instituto: registra **vendas e contratos**, gera e controla **boletos e faturas**, concilia **depósitos e remessas bancárias** e calcula **comissões** de consultores e representantes. É onde o dinheiro do IMAP entra, é cobrado e é conciliado.

Nasceu na geração ColdFusion e agora recebe **a mesma base moderna já provada nas outras seis frentes** — a renovação já começou.

## O tamanho da renovação (medido no código legado)

Números reais do código-fonte atual — a escala do trabalho:

| Métrica | SGF hoje |
|---|---|
| Páginas `.cfm` | **207** |
| Linhas de código CFML | **~49.200** |
| Hub de roteamento único | `appSgf.cfm` — **~4.000 linhas** num só arquivo |
| Front-end | template proprietário, sem build |
| Plataforma | ColdFusion + Windows Server — **fora de suporte** |

> O sistema por onde o dinheiro do Instituto entra, é cobrado e é conciliado **merece a mesma base moderna já provada nas outras frentes** — a modernização é ganho **financeiro, jurídico (LGPD) e de segurança**.

## De → Para (proposto)

| Dimensão | Antes (legado) | Depois (proposto) |
|---|---|---|
| Plataforma | ColdFusion (EOL) | **Python 3 · FastAPI · open-source** |
| Acesso a dados | camada legada | **SQLAlchemy (ORM) — consultas parametrizadas por construção** |
| Sistema operacional | Windows Server (EOL) | **Linux + Docker** |
| Front-end | template proprietário, sem build | **Astro + Vite + TypeScript** — build instantâneo, tipado |
| Banco | SQL Server (lado a lado na migração) | **PostgreSQL** (destino), lendo o mesmo banco durante o cutover |
| Licenciamento | CF + Windows (pago) | **R$ 0 (open-source)** |
| Testes automatizados | — | **pytest** — regras financeiras e geração de boleto blindadas |
| Entrega | manual | **CI + deploy conteinerizado** |
| TLS/HTTPS | manual | **Let's Encrypt automático** |

## 🏆 Ganhos desta frente

- **🚀 Modernização — ~49 mil linhas viram arquitetura.** O hub único de ~4.000 linhas dá lugar a **API FastAPI modular + front Astro/Vite tipado** — a mesma arquitetura já em produção no DIOF e no SIEJ.
- **💸 Custos — o núcleo financeiro sem licença.** Fim da licença de plataforma; **boleto e remessa (CNAB) por bibliotecas abertas** — sem componente proprietário no caminho do dinheiro.
- **🧱 Endurecimento — integridade por construção.** **Transações + validação de tipos (Pydantic) + consultas parametrizadas por padrão**: a arquitetura garante, não a disciplina.
- **🛡️ Salvaguarda — o arquivo de remessa é blindado.** Teste **"golden"** bloqueia o deploy se o CNAB mudar; **cada lançamento financeiro versionado e rastreável**, alimentando o SIEM (trilha de auditoria/LGPD).
- **🧭 Futuro — renovação módulo a módulo.** Vendas, boletos, faturas e comissões migram **um a um, lendo o mesmo banco, com rollback** — e o serviço **já está no host consolidado**.

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## 📍 Estado & próximos passos

Esta frente — anunciada no **[Pitch](../PITCH.md)** (§6, *a renovação do ERP interno*) — **já está em andamento**: o serviço novo **já entrou no host Docker consolidado**, ao lado das demais frentes, herdando toda a fundação (CI, autenticação, WAF/SIEM/SELinux). O diagnóstico do legado está completo (números acima) e a renovação segue o **método provado** nas seis frentes anteriores: módulo a módulo, lendo o mesmo banco, com rollback.

## 🧰 Tecnologias

Python · FastAPI · SQLAlchemy · Astro · Vite · TypeScript · Docker · Linux/OCI · PostgreSQL · pytest · Let's Encrypt · CI — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

## 🗺️ Roadmap

1. **Fatiar o `appSgf.cfm`** em módulos de domínio (vendas, pagamentos, boletos, faturas, comissões) e cobrir cada um com testes de caracterização.
2. **Subir a API FastAPI lendo o mesmo banco**, módulo a módulo, lado a lado com o legado.
3. **Front Astro/Vite** substituindo as telas SmartAdmin, tela a tela.
4. **Cutover gradual + rollback**; ao final, desligar mais uma parcela do Windows legado.
