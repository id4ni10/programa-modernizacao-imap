![capa](../assets/sections/transparencia.png)

# Transparência — Plataforma de ~400 Portais
> Estabilização, segurança e o novo backend (SAI3) da plataforma de transparência multi-tenant.
> *Uma frente do **[Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md)**.*

---

## O que é

**~400 portais públicos** (prefeituras, câmaras, consórcios, autarquias, fundações…) servidos por **uma única plataforma multi-tenant**. Esta frente elevou **estabilidade, organização, segurança e capacidade de evolução** — e prepara a troca do backend pelo novo **[SAI3](../sai3/)** (.NET 10 / Oracle Linux 9), sem expor o cidadão a risco.

## De → Para

| Dimensão | Antes | Depois |
|---|---|---|
| Estabilidade | falhas de JS quebravam páginas em silêncio | **~12 falhas corrigidas (1 crítica/global)** |
| Testes | inexistentes | **Cypress cobrindo ~210 rotas** |
| HTTPS | manual/parcial | **automático em ~400 domínios** (mod_md) |
| Organização do servidor | arquivos monolíticos | **por tipo de órgão** (impacto isolado) |
| Deploy | arriscado | **backup → validação → recarga sem downtime → rollback em 1 comando** |
| Backend | .NET Framework (legado) | **canário SAI3** em consórcios e autarquias |

## 🏆 Ganhos desta frente

- **🚀 Modernização — plataforma organizada por tipo de órgão.** Mudanças cirúrgicas por categoria, **raio de impacto contido**, zero perda ou duplicidade de domínios.
- **💸 Custos — HTTPS que se renova sozinho.** **~400 domínios** com certificado automático (`mod_md` + Let's Encrypt) — fim da gestão manual de centenas de certificados.
- **🧱 Endurecimento — deploy sem medo.** **Backup → validação → recarga sem downtime → rollback em 1 comando.**
- **🛡️ Salvaguarda — quebra silenciosa vira alerta.** A suíte **Cypress** varre **~210 rotas** e captura até erros que o Angular só registra no console — **bug vira alerta antes do deploy**, não reclamação de cidadão.
- **🧭 Futuro — o canário que provou o SAI3.** Consórcios e autarquias já no novo backend com **640 requisições reais → 0 incompatibilidades**; expansão **tipo a tipo** até o cutover completo, com **zero interrupção**.

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## 📍 Provas (em produção)

- **~400 portais** numa plataforma · **~210 rotas** testadas · **~400 domínios** em HTTPS automático.
- **Consórcios + autarquias** já no novo backend (SAI3), sem impacto aos demais.
- **Interrupção para o cidadão: zero.**

## 🧰 Tecnologias

Angular · Cypress · Apache (mod_md) · Let's Encrypt · Linux/OCI · **[SAI3](../sai3/)** (.NET 10) — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

## 🗺️ Roadmap

Expandir o **canário SAI3** tipo a tipo até o cutover completo; seguir a padronização e o endurecimento de segurança por categoria de órgão.
