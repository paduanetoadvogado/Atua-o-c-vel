---
name: jurisprudencia
description: Pesquisa jurisprudência para uma peça do escritório (petição, contestação, recurso). Lê a peça na pasta do caso, identifica as teses, busca julgados no TJPI e no STJ, confere cada um na fonte oficial e entrega as citações prontas para colar, no padrão das peças do escritório. Use quando o usuário pedir jurisprudência, precedentes, julgados ou "conferir os acórdãos" de um caso.
argument-hint: "[pasta do caso ou tese] — ex.: \"Petição inicial - Daniela Braga\""
---

# Pesquisa de jurisprudência

Argumento recebido: `$ARGUMENTS`

## 1. Localizar o caso

- Se o argumento for uma pasta do repositório (ex.: `Petição inicial - Daniela Braga`), leia a peça `.docx` mais recente dela com `pandoc -t plain`.
- Se for uma tese em texto livre, use-a diretamente e pergunte em qual pasta salvar o resultado.
- Sem argumento: liste as pastas de casos na raiz do repositório e pergunte qual.

## 2. Montar a lista de teses

Extraia da peça as teses que precisam de precedente. Para cada uma, anote em uma linha o que o julgado precisa dizer. Exemplo (caso Daniela Braga x BUD/Whirlpool):

1. Vício reiterado em eletrodoméstico, com trocas sucessivas sem solução → restituição da quantia paga (art. 18, §1º, II, CDC).
2. Substituição por produto recondicionado/recuperado não cumpre o art. 18, §1º, I ("perfeitas condições de uso").
3. Geladeira como produto essencial → uso imediato das alternativas (art. 18, §3º, CDC).
4. Restituição sem abatimento pelo tempo de uso.
5. Acordo no PROCON homologado não impede ação por vício superveniente; transação interpretada restritivamente (art. 843 CC) e limites da coisa julgada (art. 503 CPC).
6. Reclamação ao fornecedor obsta a decadência (art. 26, §2º, I, CDC).
7. Desvio produtivo do consumidor / dano moral por via-crúcis administrativa em vício de produto.
8. Responsabilidade solidária de comerciante e fabricante (art. 18 CDC).

Confira também todo julgado já citado na peça: número, relator, órgão julgador, data e se o conteúdo corresponde ao que a peça afirma. Liste os que não forem encontrados.

## 3. Buscar

Ordem de prioridade dos tribunais:
1. **TJPI**, especialmente as Turmas Recursais quando a ação tramitar pelo rito do Juizado; depois as Câmaras Cíveis. Fonte oficial: https://jurisprudencia.tjpi.jus.br
2. **STJ**: https://scon.stj.jus.br/SCON/ (súmulas, temas repetitivos e acórdãos da 3ª e 4ª Turmas).
3. Outros TJs só quando faltar precedente do TJPI ou do STJ, e sinalize isso.

Use WebSearch para localizar e WebFetch para abrir a página. Agregadores (JusBrasil, Migalhas, Conjur) servem só para **localizar** o julgado: confirme sempre no site oficial do tribunal. Prefira julgados dos últimos 5 anos.

Se a rede bloquear algum site oficial, diga qual e marque os julgados afetados como "não conferido na fonte oficial". Nunca apresente esses julgados como conferidos.

## 4. Regras inegociáveis

- **Nunca invente ou complete** número de processo, relator, órgão julgador, data ou trecho de ementa. Use só o que foi lido na página aberta.
- Ementa entre aspas só com transcrição literal do texto aberto. Cortes com `(...)`.
- Julgado que não puder ser conferido: liste em "Não confirmados", com o motivo. Não use na peça.
- Se a tese não tiver precedente favorável, diga isso. Se encontrar precedente **contrário** relevante, informe-o também, porque o advogado precisa saber.

## 5. Entregar

Salve na pasta do caso o arquivo `Pesquisa de jurisprudência - <Nome do cliente>.docx`, com timbre e formatação iguais aos da peça do caso (Arial 12, recuo de 1ª linha, ementas recuadas em itálico, fonte 10). Use a skill de docx e parta do `.docx` da própria peça para manter cabeçalho e rodapé. Estrutura:

1. **Resumo**: uma tabela com tese, quantidade de julgados encontrados e o mais forte de cada uma.
2. **Por tese**: para cada julgado, um parágrafo de uma ou duas linhas dizendo por que serve e onde encaixa na peça (tópico), seguido da citação pronta no padrão do escritório:

   > EMENTA (trecho literal relevante) (...) (TJPI – RECURSO INOMINADO CÍVEL nº 0000000-00.0000.8.18.0000 – Relator(a): NOME – 3ª Turma Recursal – Julgamento: dd/mm/aaaa) (grifo nosso)

   Logo abaixo, o link da página oficial onde foi conferido.
3. **Conferência dos julgados já citados na peça**: tabela com julgado, situação (confirmado / dados divergentes / não encontrado) e correção sugerida.
4. **Não confirmados**: julgados localizados apenas em agregadores, com o motivo.

Depois, faça commit da pesquisa na branch atual e envie o arquivo ao usuário. **Não altere a peça** sem pedido expresso. Ao final, ofereça inserir os julgados confirmados nos pontos marcados com `[conferir ...]` ou `[inserir número do REsp ...]`.
