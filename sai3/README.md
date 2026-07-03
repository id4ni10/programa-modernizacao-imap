# SAI3 — Modernização do Portal da Transparência
> De .NET Framework 4.6.1 / IIS / Windows → **.NET 10 / Oracle Linux 9** · Junho/2026
> *Uma frente do [Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md).*

![capa](assets/hero.png)

## 👉 Comece por aqui
**[`apresentacao-sai3.md`](apresentacao-sai3.md)** — o documento **único e consolidado**, na ordem de apresentação, com as imagens. **É a fonte canônica.**

### Material de apoio (mesmos fatos, outros formatos)
| Arquivo | Para quê |
|---|---|
| [`slides-migracao-sai3.md`](slides-migracao-sai3.md) | deck, um impacto por tela |
| [`sai2-vs-sai3-vantagens.md`](sai2-vs-sai3-vantagens.md) | deep-dive das 12 vantagens + roadmap do banco |
| `assets/` | imagens (capa, segurança, antes/depois, fundação) |

## 🎯 Os fatos principais
- 🟢 **640 requisições reais testadas · 0 incompatibilidades** (SAI3 × SAI2, dados reais, 2 municípios).
- 🟢 **Custo de licença ≈ R$ 0** — SO, runtime, WAF, SIEM e bibliotecas: tudo gratuito/open-source.
- 🟢 **Segurança reforçada** — WAF, SIEM (Wazuh), SELinux, TLS automático.
- 🟢 **Rollback em minutos** — o legado segue intacto.
- 🟢 **Já em produção** — canário em consórcios e autarquias, expandindo tipo a tipo.
- 🔜 **Banco + arquivos**: próxima frente do roadmap (ver [`infraestrutura/`](../infraestrutura/RESUMO-EXECUTIVO-infraestrutura.md)).
