# 🔒 Recuperação de Site WordPress Hackeado - Balaio Nordeste

📅 **Data**: 15/03/2025  
👤 **Responsável**: Pedro Michael Bezerra de Oliveira  
🏛️ **Cliente**: Associação Cultural Balaio Nordeste  
🌐 **Site Afetado**: [balaionordeste.org](http://balaionordeste.org)

---

## 🧠 Contexto

O site da Associação Cultural Balaio Nordeste foi meu objeto de estudo e aplicação prática durante o Trabalho de Conclusão de Curso em Informática (jun-dez/2024), no qual atuei na manutenção e atualização do site institucional.

Em março de 2025, fui novamente acionado pela instituição após a identificação de um possível ataque ao site. Este relatório descreve o processo completo de análise, recuperação e prevenção de futuras vulnerabilidades.

---

## ❗ Descrição do Problema

O site apresentava:
- Comportamentos anormais no carregamento.
- Exibição de conteúdo não autorizado.
- Lentidão e redirecionamentos suspeitos.

Um ataque havia comprometido a integridade do site, exigindo ações rápidas de correção e blindagem.

---

## 🔧 Etapas Realizadas

### 1. Diagnóstico e Acesso ao WordPress
- Acesso via painel administrativo com credenciais seguras.
- Análise de contas de usuário suspeitas.
- Verificação de temas e plugins instalados.
- Atualização para as versões mais recentes do CMS, plugins e temas.

### 2. Inspeção via FTP
- Conexão segura com FileZilla.
- Análise de permissões de arquivos/pastas.
- Varredura manual das principais estruturas do site (wp-content, wp-includes).

### 3. Identificação de Códigos Maliciosos
- Uso de ferramentas online para análise de malware.
- Detecção de script injetado no `header.php`, com comportamento malicioso (provável backdoor via plugin desatualizado).
- Análise de arquivos `.php`, com base na estrutura do WordPress, para identificar funções obscuras, eval(), base64_decode() e outras práticas comuns em malwares.

### 4. Limpeza e Correção
- Remoção do código malicioso.
- Restauração de arquivos principais a partir de versões limpas.
- Revisão manual de todos os arquivos modificados recentemente.
- Verificação de banco de dados (posts e options) para rastrear payloads ocultos.

---

## ✅ Resultados Obtidos

✔️ Site restaurado com sucesso.  
✔️ Navegação e conteúdo seguros.  
✔️ Arquivos e banco de dados limpos.  
✔️ Medidas de segurança aplicadas para mitigar novos ataques.

---

## 🧰 Tecnologias e Ferramentas Utilizadas

| Área | Ferramentas / Tecnologias |
|------|----------------------------|
| CMS  | WordPress |
| FTP  | FileZilla |
| Segurança | Scanner de malware (Sucuri SiteCheck), análise manual |
| Linguagens | PHP, HTML, JavaScript |
| Análise de Código | Identificação de funções maliciosas (`eval`, `base64_decode`, `str_rot13`, `preg_replace` com /e) |
| Banco de Dados | MySQL (via painel do provedor) |
| Sistema de Arquivos | Navegação por diretórios e permissões Linux-style |

---

## 🔐 Boas Práticas e Recomendações

- ✅ Atualizar sempre o WordPress e seus componentes.
- ✅ Utilizar plugins e temas verificados e confiáveis.
- ✅ Manter backups automáticos e frequentes.
- ✅ Utilizar autenticação em duas etapas (2FA).
- ✅ Monitorar o site com ferramentas de segurança e logs.

---

## 📂 Organização do Repositório

