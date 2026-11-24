# Aula 01 — Linux: do kernel à coleta de métricas

[Voltar à aula](README.md)

## Objetivos
Distinguir kernel e aplicações, interpretar métricas de CPU e memória, reconhecer limites de observação e produzir um relatório de coleta manual. Não é necessário conhecer Python nesta aula.

## 1. A missão
Construir um agente que coleta indicadores de um servidor Linux e produz JSON. Nesta aula, vamos compreender de onde vêm os indicadores, antes de escrever o agente. A primeira entrega será um relatório manual reproduzível, com evidências obtidas do sistema.

## 2. Kernel e espaço de usuário
O kernel administra CPU, memória, dispositivos e processos. Aplicações executam normalmente em espaço de usuário e solicitam serviços ao kernel por chamadas de sistema. Uma biblioteca pode encapsular essas chamadas: open, read e close são exemplos. O shell é uma aplicação, não o kernel.

## 3. Interfaces de observação
/proc é um sistema de arquivos virtual que expõe informações do kernel e dos processos; /sys expõe objetos e atributos do kernel, inclusive dispositivos. Ler um arquivo virtual não equivale necessariamente a ler um bloco de disco. Muitos valores são gerados no momento da leitura.

## 4. Processos e threads
Um processo possui um espaço de endereçamento e recursos; threads de um mesmo processo compartilham parte desses recursos e são escalonadas individualmente. Uma thread pode executar enquanto outra aguarda uma operação. O estado R indica execução ou espera por CPU; D indica espera ininterruptível, frequentemente por I/O.

## 5. CPU: contadores e taxas
A linha cpu de /proc/stat contém contadores acumulados de tempo em diferentes estados. Uma amostra isolada não informa a utilização durante um intervalo. Colete duas amostras e calcule deltas. Para uma aproximação da atividade, subtraia do total o delta de idle e iowait; não some guest e guest_nice novamente, pois já integram outros campos. Iowait tem limitações e não mede diretamente latência de disco.

Exemplo: delta total de 800 ticks, idle de 400 e iowait de 80. A atividade estimada é (800 − 400 − 80)/800 = 40%.

## 6. Load average
As três médias de carga correspondem a 1, 5 e 15 minutos, com suavização exponencial. No Linux, incluem tarefas executáveis e tarefas em espera ininterruptível. Uma carga de 12 em uma máquina de 8 CPUs lógicas sugere investigar filas, mas não prova saturação de CPU. Use vmstat e iostat para distinguir hipóteses.

## 7. Memória
MemFree indica páginas livres; MemAvailable estima a memória disponível para novas aplicações sem swap. O cache pode ser recuperado sob pressão, mas nem todo cache é recuperável. A métrica inicial do agente deve usar MemAvailable e MemTotal, preservando as unidades.

## 8. Limites e escopo
Um container compartilha o kernel do hospedeiro. Namespaces isolam visões de recursos; cgroups contabilizam e limitam recursos. A leitura de /proc pode refletir o host, não o limite do container. Em cgroups v2, memory.max e cpu.max ajudam a entender limites. Nesta missão, o agente executará no host.

## 9. Laboratório e validação
Execute o [laboratório](laboratorio.md) e responda aos [exercícios](exercicios.md).

## 10. Próxima etapa
Após validar o relatório, aprenderemos Python: leitura de arquivos, conversão de tipos, funções, tratamento de erros e serialização JSON. O agente deverá distinguir falha de coleta de valor zero, registrar timestamp UTC e identificar o host.

## Referências
- [Linux kernel: proc filesystem](https://docs.kernel.org/filesystems/proc.html)
- [Linux kernel: cgroup v2](https://docs.kernel.org/admin-guide/cgroup-v2.html)
- [proc(5)](https://man7.org/linux/man-pages/man5/proc.5.html)
