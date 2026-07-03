![capa](diof-og.png)

# Diário Inteligente (DIOF)
> Sistema operador do Diário Oficial — diagramação e publicação de atos oficiais.
> **De ColdFusion 11 → Python + FastAPI.** Em produção em `diof.imap.org.br`.
> *Uma frente do **[Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md)**.*

---

## O que é

O DIOF é a metade **operadora** do Diário Oficial: recebe os anexos, **diagrama** a edição do dia e a publica. Rodava em **ColdFusion 11** sobre **Windows Server 2012 R2** (ambos fora de suporte), com um motor de PDF preso a componentes Windows.

## De → Para

| Dimensão | Antes (legado) | Depois (Diário Inteligente) |
|---|---|---|
| Runtime | ColdFusion 11 (fim de vida 2021) | **Python + FastAPI** (mantido) |
| Sistema operacional | Windows Server 2012 R2 | **Linux / OCI (contêiner)** |
| Motor de documentos | componentes Windows proprietários | **PyMuPDF + Chromium + LibreOffice** |
| Licenciamento | Adobe CF + Windows (pago) | **R$ 0 (open-source)** |
| QA de cutover | inexistente | **portão de fidelidade (SSIM + texto)** |
| Acessibilidade | app preso ao desktop | **web responsiva (e-MAG/WCAG) + leitura por voz** |

## 🏆 Ganhos desta frente

- **🚀 Modernização — um clique para diagramar.** O painel, **idêntico ao legado**, busca os anexos certos por data e **monta a edição do dia sozinho**; **arrastar-e-soltar** para ordenar. O operador não reaprende nada — só ganha velocidade.
- **💸 Custos — motor de documentos 100% aberto.** **PyMuPDF · Chromium · LibreOffice** substituem os componentes proprietários de geração de PDF — essa licença desaparece, e o serviço divide o host consolidado.
- **🧱 Endurecimento — edição gerada por código.** Cada edição sai de um **pipeline versionado, reproduzível e testável** — não de um componente caixa-preta.
- **🛡️ Salvaguarda — portão de fidelidade.** Cada edição nova é comparada **pixel a pixel (SSIM) + camada de texto** com a referência. **Só publica quem passa.** A integridade do ato oficial — que tem **valor legal** — é garantida por máquina, edição a edição.
- **🧭 Futuro — provado em escala.** **637 clientes** e edições multi-fonte reais (PDF + Word + imagem) já processadas; cutover **cliente a cliente, atrás do portão**, e **leitura por voz (TTS)** no leitor público — acessibilidade real (**LBI**).

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## 📍 Provas (em produção)

- Produção pública: **`diof.imap.org.br`** (HTTPS, certificado válido, auto-deploy).
- **Painel batendo exatamente com o legado** (contagens idênticas por status).
- **Diagramação real** de edições multi-fonte (PDF + Word + imagem) montadas pelo motor novo.
- Já rodou **em escala** (centenas de edições, **637 clientes**).

## 🧰 Tecnologias

Python · FastAPI · PyMuPDF · Chromium · LibreOffice · Docker · Linux/OCI — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

## 🗺️ Roadmap

Integrar a **publicação** do PDF → persistir o layout → **cutover por cliente** atrás do portão de fidelidade → **desligar ColdFusion 11 + Windows Server 2012 R2**.
