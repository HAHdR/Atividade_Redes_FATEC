# Atividade Prática: Máscaras de Sub-Rede e Endereçamento IP

**Nome:** Henrique Abreu Hollanda da Rocha
**Data:** 27/03/2026

---

## Caminho A — FLSM (Máscara Fixa)

### A1. Escolha da Máscara Única (Etapa 1)

- **Setor com maior número de estações:** Produção
- **Total de endereços necessários nesse setor:** (estações + gateway + rede + broadcast): 25 + 1 + 1 + 1 = 28
- **Bits de host necessários (n):** 5
- **Máscara escolhida para todas as sub-redes:** 255.255.255.224 /27
- **Tamanho do bloco (2ⁿ):** 32

### A2. Tabela de Planejamento de Sub-Redes — FLSM (Etapa 2)

Distribua as sub-redes sequencialmente a partir de `200.221.30.0`, utilizando a **mesma máscara** para todos os setores:

| Setor | Estações | Máscara de Sub-Rede | CIDR | End. de Rede | Primeiro IP Utilizável | Último IP Utilizável | End. de Broadcast |
|---|---|---|---|---|---|---|---|
| Produção | 25 | 255.255.255.224 | /27 | 200.221.30.0 | 200.221.30.1 | 200.221.30.30 | 200.221.30.31 |
| Vendas | 20 | 255.255.255.224 | /27 | 200.221.30.32 | 200.221.30.33 | 200.221.30.62 | 200.221.30.63 |
| RH | 5 | 255.255.255.224 | /27 | 200.221.30.64 | 200.221.30.65 | 200.221.30.94 | 200.221.30.95 |
| Marketing | 5 | 255.255.255.224 | /27 | 200.221.30.96 | 200.221.30.97 | 200.221.30.126 | 200.221.30.127 |
| Gerência | 2 | 255.255.255.224 | /27 | 200.221.30.128 | 200.221.30.129 | 200.221.30.158 | 200.221.30.159 |

### A3. Verificação — FLSM (Etapa 3)

#### A3.1 Nenhuma sub-rede se sobrepõe a outra?

Não, por conta da distribuição de cada bloco que respeita o tamanho das subredes.

#### A3.2 Cada sub-rede comporta todos os hosts necessários?

Sim, pois a capacidade máxima de IPs de cada subrede supera a quantidade de hosts/estações.

#### A3.3 Todos os endereços estão dentro da faixa `200.221.30.0/24`?

Sim. O último endereço de broadcast não ultrapassa 200.221.30.255.

#### A3.4 Quantos endereços ficaram sem uso (fora das sub-redes)?

256 - 160 = 96.

#### A3.5 Quantos endereços foram desperdiçados dentro das sub-redes?

Produção: 30 - (25 + 1) = 4
Vendas: 30 - (20 + 1) = 9
RH: 30 - (5 + 1) = 24
Marketing: 30 - (5 + 1) = 24
Gerência: 30 - (2 + 1) = 27

4 + 9 + 24 + 24 + 27 = 88.

| Setor | Hosts Utilizáveis | Estações + Gateway | Desperdício |
|---|---|---|---|
| Produção | 30 | 26 | 4 |
| Vendas | 30 | 21 | 9 |
| RH | 30 | 6 | 24 |
| Marketing | 30 | 6 | 24 |
| Gerência | 30 | 3 | 27 |
| **Total** | 150 | 62 | 88 |

---

## Caminho B — VLSM (Máscara Variável)

### B1. Análise de Requisitos por Setor (Etapa 1)

> **Lembrete:** Ordene os setores do maior para o menor número de estações.

#### Produção (25 estações)

- **Total de endereços necessários:** 25 + 1 + 1 + 1 = 28
- **Bits de host necessários (n):** 5
- **Máscara de sub-rede:** 255.255.255.224 /27
- **Tamanho do bloco (2ⁿ):** 32

#### Vendas (20 estações)

- **Total de endereços necessários:** 20 + 1 + 1 + 1 = 23
- **Bits de host necessários (n):** 5
- **Máscara de sub-rede:** 255.255.255.224 /27
- **Tamanho do bloco (2ⁿ):** 32

#### RH (5 estações)

- **Total de endereços necessários:** 5 + 1 + 1 + 1 = 8
- **Bits de host necessários (n):** 3
- **Máscara de sub-rede:** 255.255.255.248 /29
- **Tamanho do bloco (2ⁿ):** 8

#### Marketing (5 estações)

- **Total de endereços necessários:** 5 + 1 + 1 + 1 = 8
- **Bits de host necessários (n):** 3
- **Máscara de sub-rede:** 255.255.255.248 /29
- **Tamanho do bloco (2ⁿ):** 8

#### Gerência (2 estações)

- **Total de endereços necessários:** 2 + 1 + 1 + 1 = 5
- **Bits de host necessários (n):** 3
- **Máscara de sub-rede:** 255.255.255.248 /29
- **Tamanho do bloco (2ⁿ):** 8

### B2. Tabela de Planejamento de Sub-Redes — VLSM (Etapa 2)

Distribua as sub-redes sequencialmente a partir de `200.221.30.0`, utilizando a **máscara mais específica** para cada setor:

| Setor | Estações | Máscara de Sub-Rede | CIDR | End. de Rede | Primeiro IP Utilizável | Último IP Utilizável | End. de Broadcast |
|---|---|---|---|---|---|---|---|
| Produção | 25 | 255.255.255.224 | /27 | 200.221.30.0 | 200.221.30.1 | 200.221.30.30 | 200.221.30.31 |
| Vendas | 20 | 255.255.255.224 | /27 | 200.221.30.32 | 200.221.30.33 | 200.221.30.62 | 200.221.30.63 |
| RH | 5 | 255.255.255.248 | /29 | 200.221.30.64 | 200.221.30.65 | 200.221.30.70 | 200.221.30.71 |
| Marketing | 5 | 255.255.255.248 | /29 |200.221.30.72 | 200.221.30.73 | 200.221.30.78 | 200.221.30.79 |
| Gerência | 2 | 255.255.255.248 | /29 | 200.221.30.80 | 200.221.30.81 | 200.221.30.86 | 200.221.30.87 |

### B3. Verificação — VLSM (Etapa 3)

#### B3.1 Nenhuma sub-rede se sobrepõe a outra?

Nenhuma rede se sobrepõe a outra. Os blocos foram distribuídos de maneira a respeitar o tamanho das subredes. Cada rede começa logo após o término da anterior.

#### B3.2 Cada sub-rede comporta todos os hosts necessários?

Sim, pois cada subrede respeita o tamanho de seu bloco, comportando todos os hosts necessários.

Produção: 30 IPs utilizáveis para 26 dispositivos.
Vendas: 30 IPs utilizáveis para 21 dispositivos.
RH: 6 IPs utilizáveis para 6 dispositivos.
Marketing: 6 IPs utilizáveis para 6 dispositivos.
Gerência: 6 IPs utilizáveis para 3 dispositivos.

#### B3.3 Todos os endereços estão dentro da faixa `200.221.30.0/24`?

Sím, todos os endereços estão nessa faixa, que vai de 200.221.30.0 até 200.221.30.255. O último endereço de broadcast alocado é 200.221.30.87, que está dentro do intervalo.

#### B3.4 Quantos endereços ficaram sem uso?

256 - (32 + 32 + 8 + 8 + 8) = 168.

---

## Comparação FLSM × VLSM (Etapa 4)

Preencha a tabela abaixo com os totais obtidos em cada caminho:

| Métrica | FLSM | VLSM |
|---------|------|------|
| Máscara(s) utilizada(s) | 1 | 2 |
| Total de endereços alocados | 160 | 88 |
| Total de endereços sem uso (fora das sub-redes) | 96 | 168 |
| Total de endereços desperdiçados (dentro das sub-redes) | 88 | 16 |

---

## Questões para Reflexão

### Questão 1

**Com base na tabela comparativa, explique por que o VLSM é mais eficiente que o FLSM no aproveitamento de endereços IP. Em quais cenários o FLSM ainda poderia ser a melhor escolha?**

O VLSM é mais eficiente porque usa máscaras diferentes para cada setor, evitando desperdício de IPs. Já o FLSM usa uma única máscara, o que gera desperdício. O FLSM pode ser melhor em redes simples, com tamanhos iguais, por ser mais fácil de configurar.

### Questão 2

**Considerando a solução VLSM, se a empresa precisasse criar um novo departamento com 10 estações, seria possível acomodá-lo na faixa restante? Justifique indicando a sub-rede que seria utilizada.**

Sim. O novo setor precisa de 16 endereços, que é o tamanho do bloco. Pode ser alocado a partir de 200.221.30.88, que ainda está livre na faixa restante, indo até 200.221.30.103, que também está dentro da faixa.

### Questão 3

**Considerando a solução FLSM, seria possível acomodar esse mesmo novo departamento na faixa restante? Compare com a resposta anterior.**

Sim. No FLSM ainda há espaço disponível, mas o setor receberia uma sub-rede /27 (32 endereços), gerando mais desperdício do que no VLSM.

### Questão 4

**Qual é a função do endereço de broadcast em uma sub-rede? Cite um exemplo de protocolo que o utiliza.**

O broadcast envia dados para todos os dispositivos da sub-rede. Um exemplo é o protocolo ARP.

### Questão 5

**Em uma rede real, por que é importante reservar pelo menos um endereço IP para o gateway da sub-rede?**

O gateway permite a comunicação com outras redes. Sem ele, os dispositivos só se comunicam dentro da própria sub-rede.
