# Aula 01 — Linux: do kernel à coleta de métricas

[← Sumário do livro](../../README.md)

## Missão 01

Construir um agente Python que obtenha métricas de CPU, memória, disco e processos, estruturando os resultados em JSON. Nesta aula, o foco é interpretar CPU e memória e produzir evidências manuais.

## Materiais disponíveis

| Material | Acesso |
|---|---|
| Apostila | [Capítulo em Markdown](apostila.md) |
| Resumo | [Revisão rápida](resumo.md) |
| Podcast | [Roteiro integral da narração](roteiro_audio.txt) |
| Flashcards | [TSV para Anki](flashcards.tsv) |
| Exercícios | [Questões de fixação](exercicios.md) |
| Laboratório | [Roteiro prático](laboratorio.md) |

## Arquivos originais a incorporar

Os arquivos do pacote original existem, mas ainda não foram transferidos ao GitHub: apostila.pdf, apresentacao.pptx, apresentacao.pdf, aula.mp3 e resumo.pdf. O pacote engineering-academy.zip também está pendente. Não há URL pública permanente confirmada para esses arquivos.

## Critérios de aceitação da missão
- Coletar métricas sem exigir root para operação normal.
- Documentar unidades e significado de cada indicador.
- Tratar falhas de leitura e produzir JSON válido.
- Comparar resultados com ferramentas Linux e explicar diferenças.
- Implementar testes e defender decisões técnicas.

## Referências
- [Documentação Linux: procfs](https://docs.kernel.org/filesystems/proc.html)
- [Documentação Linux: cgroups v2](https://docs.kernel.org/admin-guide/cgroup-v2.html)

Próxima aula: leitura de arquivos e tratamento de dados em Python (planejada).
