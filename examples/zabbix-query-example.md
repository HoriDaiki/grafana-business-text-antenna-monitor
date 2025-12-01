# Exemplos de Consultas Zabbix para Monitoramento de ICMP Ping

## Exemplo 1: Consulta Simples de ICMP Ping
Esta consulta retorna o status do ping de um dispositivo:

```sql
SELECT * FROM icmp_ping WHERE host = 'hostname';
```

## Exemplo 2: Consulta com Tempo de Resposta
Abaixo está uma consulta que retorna o tempo médio de resposta de ping:

```sql
SELECT avg(response_time) as tempo_medio_resposta FROM icmp_ping WHERE host = 'hostname' AND time >= now() - interval '1 hour';
```

## Exemplo 3: Monitorar Perdas de Pacote
Uma consulta para verificar a perda de pacotes nos últimos 10 minutos:

```sql
SELECT count(*) FILTER (WHERE response_status = 'timeout') as perdas_de_pacote FROM icmp_ping WHERE host = 'hostname' AND time >= now() - interval '10 minutes';
```

## Exemplo 4: Alertas Baseados em ICMP Ping
Exemplo de consulta para alertar se o ping falhar:

```sql
SELECT * FROM icmp_ping WHERE host = 'hostname' AND response_status = 'timeout' AND time >= now() - interval '5 minutes';
```
``