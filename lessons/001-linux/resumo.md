# Revisão rápida — Aula 01

- Kernel: administra recursos; aplicações acessam serviços por chamadas de sistema.
- /proc e /sys: interfaces virtuais de observação.
- Threads são escalonadas individualmente; R indica execução ou espera de CPU; D, espera ininterruptível.
- CPU: calcular deltas de duas amostras de /proc/stat, sem contar guest duas vezes.
- Load average não é porcentagem de CPU; inclui tarefas executáveis e em espera ininterruptível.
- MemAvailable estima memória disponível sem swap.
- Namespaces isolam visões; cgroups contabilizam e limitam recursos.
- Compare métricas com ferramentas do sistema e documente unidades, intervalo e escopo.

[Capítulo completo](apostila.md) · [Laboratório](laboratorio.md) · [Exercícios](exercicios.md)
