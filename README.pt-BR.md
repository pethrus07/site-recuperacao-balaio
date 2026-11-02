Português | [English](README.md)

# Recuperação de site WordPress invadido

> **Arquivado (2026-11).** Entrega pontual de março de 2025. Não há código aqui, só o registro do serviço.

## O que foi

O site WordPress de uma associação cultural passou a carregar devagar, a mostrar conteúdo que ninguém tinha publicado e a redirecionar visitantes para páginas suspeitas. Eu conhecia bem o site porque tinha cuidado dele no meu trabalho de conclusão de curso, em 2024, e a associação me chamou de volta.

O que foi feito:

1. **Diagnóstico pelo painel.** Contas de usuário suspeitas revisadas, temas e plugins listados, WordPress, plugins e temas atualizados.
2. **Inspeção dos arquivos por FTP.** Permissões conferidas e `wp-content` e `wp-includes` revisados à mão.
3. **Achar o código malicioso.** Um scanner online (Sucuri SiteCheck) e leitura manual dos arquivos PHP atrás de `eval`, `base64_decode`, `str_rot13` e `preg_replace` com `/e`. Apareceu um script injetado no `header.php` do tema, provavelmente uma porta dos fundos por um plugin desatualizado.
4. **Limpeza.** Código malicioso removido, arquivos do núcleo restaurados de cópias limpas, arquivos modificados recentemente revisados, banco (posts e options) conferido atrás de carga escondida.

Resultado: site restaurado, conteúdo e navegação limpos, e recomendações deixadas com a associação (manter tudo atualizado, só plugin confiável, backup automático, login em duas etapas, monitoramento).

Este repositório também absorve um segundo registro, mais curto, do mesmo serviço (`Balaio-unphising`), que tinha só uma nota de uma linha.

## O que ficou de aprendizado

- **Ler o código, não só o scanner.** O scanner apontou o site; o script injetado foi confirmado lendo os arquivos PHP à mão.
- **Arquivo limpo não basta.** Carga maliciosa também se esconde no banco, nos posts e no `wp_options`.
- **A porta de entrada importa mais que a faxina.** Sem atualizar o plugin desatualizado, o mesmo ataque voltaria.
- **Prevenir sai mais barato.** Atualização, backup e login em duas etapas teriam evitado quase todo o trabalho.

## Licença

Todos os direitos reservados. Publicado como portfólio; não licenciado para reuso. Veja o arquivo [LICENSE](LICENSE).
