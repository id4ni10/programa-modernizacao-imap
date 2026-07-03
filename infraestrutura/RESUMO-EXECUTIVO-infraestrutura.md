![capa](../assets/sections/infraestrutura.png)

# Infraestrutura — Banco de Dados e Arquivos
> A **última fundação legada**: tirar o **SQL Server** e o **servidor de arquivos (FTP)** do **Windows** e levá-los para **Oracle Linux 9**.
> **Próxima frente do [Programa de Modernização IMAP](../PROGRAMA-MODERNIZACAO-IMAP.md).** Em planejamento.

---

## Escopo desta frente

As aplicações já foram modernizadas (SAI3, DIOF, NFS-e, SIEJ…). Esta frente leva as duas peças de **infraestrutura compartilhada** para a mesma base moderna:

| Componente | Movimento | Ganho |
|---|---|---|
| **Banco de dados** | **SQL Server 2017** → **Linux (OL9)** | mesma engine, sem reescrita; **elimina licença Windows Server + CALs** |
| **Servidor de arquivos** | FTP → **SFTP / Object Storage em Linux** (mídias, documentos, PDFs de atos oficiais) | **transferência cifrada de ponta a ponta**, escalável |

> É a frente que **fecha o ciclo do programa**: unifica a base, elimina o que resta de licença desnecessária e simplifica a operação.

---

## 🗄️ Migração do Banco de Dados (SQL Server → Oracle Linux 9)

**Fato que facilita tudo:** o banco já é **SQL Server 2017**, que **roda nativamente em Linux**. Ou seja, dá para concluir a migração **sem trocar de versão e sem reescrever** nada.

**Caminho, do menor ao maior ganho:**

1. **SQL Server em Linux (OL9)** — *menor atrito.* Mesma versão, **mesmos stored procedures**, mesma aplicação. **Elimina a licença de Windows Server + CALs** no host de banco. Mantém 100% de compatibilidade.

**Ganhos:** base unificada em Linux · patches/segurança contínuos · consolidação · backups e HA modernos · **caminho para custo de licença R$ 0**.

---

## 📁 Migração do Servidor de Arquivos (FTP → Linux)

O servidor de arquivos serve mídias, documentos e **PDFs de atos oficiais**. Modernizá-lo unifica a stack em Linux e **eleva o padrão da transferência** — cifragem de ponta a ponta e integração direta com a stack em contêineres.

**Caminho:**

1. **SFTP / FTPS em Linux** — transferência **cifrada**, mesmo modelo de pastas, integra direto com os apps já em Linux.
2. **Armazenamento de objetos** (OCI Object Storage / S3-compatível) com **URLs assinadas** — escalável, com CDN e sem servidor de arquivos para manter.

**Ganhos:** stack unificada em Linux · **transferência cifrada** (segurança/LGPD) · escalabilidade · integração natural com a stack em contêineres. *A camada de acesso a arquivos das aplicações já foi reescrita em biblioteca moderna (FluentFTP), então repontar para o novo destino é simples.*

---

## 🏆 Ganhos desta frente

- **🚀 Modernização — migração sem reescrita.** O **SQL Server 2017 roda nativamente em Linux**: mesma engine, mesmos *stored procedures*, mesma aplicação — o passo é de **baixo atrito por natureza**.
- **💸 Custos — a última licença desnecessária.** Elimina **Windows Server + CALs** nos hosts de banco e arquivos, e abre o caminho para **PostgreSQL (licença R$ 0)**.
- **🧱 Endurecimento — arquivos de primeira classe.** **SFTP/FTPS** ou **Object Storage com URLs assinadas**, host sob **SELinux**, superfície mínima.
- **🛡️ Salvaguarda — cifragem de ponta a ponta.** Mídias, documentos e **PDFs de atos oficiais** trafegam cifrados — padrão atual de segurança/LGPD.
- **🧭 Futuro — fecha o ciclo com método.** Réplica/espelho, lado a lado, **a mesma suíte que validou o SAI3 (640 requisições)** e rollback — o encerramento do programa com a régua que já provou funcionar.

> ♻️ Somam-se os **benefícios comuns do programa** — **licença R$ 0**, base mantida e com patches, **Linux + Docker + OCI**, **segurança em profundidade** (WAF · SIEM · SELinux · TLS automático), **migração incremental e reversível**, mão de obra abundante, **sem parar a operação** — descritos uma única vez no **[Programa, §3](../PROGRAMA-MODERNIZACAO-IMAP.md)**.

## ⚠️ Riscos e mitigação

| Risco | Mitigação |
|---|---|
| Diferenças de comportamento do banco | **SQL Server em Linux** mantém a mesma engine → sem risco de reescrita. Validação com a **mesma suíte usada no SAI3** (640 requisições). |
| Downtime na virada | Migração com **réplica/espelho**, cutover em janela e **rollback** imediato para o ambiente anterior. |
| Repontar os apps para o novo FTP | Camada de arquivos já em biblioteca moderna → troca de destino simples. |

---

## 🗺️ Próximos passos (proposta)

1. **Provisionar SQL Server em Linux/contêiner (OL9)** e replicar o catálogo `SAI`.
2. **Validar** com a suíte de compatibilidade já existente (a mesma que comprovou o SAI3).
3. **Cutover do banco** em janela, com réplica e rollback.
4. **Subir SFTP / Object Storage** e **repontar** os apps (Handler de mídias/documentos).
5. **Desativar os hosts antigos** — encerrando o ciclo do programa.

---

## 🧰 Tecnologias

SQL Server (em Linux) · PostgreSQL (roadmap) · Docker · Oracle Linux 9 · OCI Object Storage · SFTP/FTPS — impacto de cada uma em **[TECNOLOGIAS.md](../TECNOLOGIAS.md)**.

---

> **Em resumo:** esta é a frente que **fecha o ciclo** da modernização — leva as duas últimas peças (banco e arquivos) para a base unificada e elimina o que resta de licença desnecessária, e abre caminho para um banco **open-source (licença R$ 0)** no futuro. O SQL Server já é 2017 (roda em Linux), então o primeiro passo é **de baixo atrito**.
