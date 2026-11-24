# Laboratório 01 — Observação do Linux

Execute em ambiente de teste, sem alterar configurações.

```bash
nproc
lscpu
uptime
head -n 5 /proc/stat
sleep 1
head -n 5 /proc/stat
grep -E 'MemTotal|MemAvailable' /proc/meminfo
vmstat 1 5
```

## Entrega
Registre CPU lógica, load average, memória total e disponível, duas amostras de CPU e intervalo. Explique a diferença entre contador e taxa. A primeira linha de vmstat pode refletir médias desde o boot. Compare as linhas seguintes.

## Critérios
- Unidades corretas e origem identificada.
- Não confundir load com utilização.
- Explicar a diferença entre host e container.
- Registrar limitações e hipóteses sem alterar o ambiente.
