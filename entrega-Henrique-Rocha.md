# Atividade Prática: Máscaras de Sub-Rede e Endereçamento IP

**Nome:** *(seu nome completo)*
**Data:** *(data de entrega)*

---

## Caminho A — FLSM (Máscara Fixa)

### A1. Escolha da Máscara Única (Etapa 1)

- **Setor com maior número de estações:** *(preencher)*
- **Total de endereços necessários nesse setor** (estações + gateway + rede + broadcast): *(preencher)*
- **Bits de host necessários (n):** *(preencher)*
- **Máscara escolhida para todas as sub-redes:** *(decimal)* / *(CIDR)*
- **Tamanho do bloco (2ⁿ):** *(preencher)*

### A2. Tabela de Planejamento de Sub-Redes — FLSM (Etapa 2)

Distribua as sub-redes sequencialmente a partir de `200.221.30.0`, utilizando a **mesma máscara** para todos os setores:

| Setor | Estações | Máscara de Sub-Rede | CIDR | End. de Rede | Primeiro IP Utilizável | Último IP Utilizável | End. de Broadcast |
|---|---|---|---|---|---|---|---|
| Produção | 25 | | | | | | |
| Vendas | 20 | | | | | | |
| RH | 5 | | | | | | |
| Marketing | 5 | | | | | | |
| Gerência | 2 | | | | | | |

### A3. Verificação — FLSM (Etapa 3)

#### A3.1 Nenhuma sub-rede se sobrepõe a outra?

*(Responda aqui. Demonstre que os blocos são contíguos e sem conflito.)*

#### A3.2 Cada sub-rede comporta todos os hosts necessários?

*(Responda aqui. Considere estações + gateway.)*

#### A3.3 Todos os endereços estão dentro da faixa `200.221.30.0/24`?

*(Responda aqui. Indique qual é o último endereço de broadcast alocado.)*

#### A3.4 Quantos endereços ficaram sem uso (fora das sub-redes)?

*(Responda aqui. Calcule: 256 − total de endereços alocados.)*

#### A3.5 Quantos endereços foram desperdiçados dentro das sub-redes?

*(Para cada setor, calcule: hosts utilizáveis da sub-rede − (estações + gateway). Some os valores.)*

| Setor | Hosts Utilizáveis | Estações + Gateway | Desperdício |
|---|---|---|---|
| Produção | | | |
| Vendas | | | |
| RH | | | |
| Marketing | | | |
| Gerência | | | |
| **Total** | | | |

---

## Caminho B — VLSM (Máscara Variável)

### B1. Análise de Requisitos por Setor (Etapa 1)

> **Lembrete:** Ordene os setores do maior para o menor número de estações.

#### Produção (25 estações)

- **Total de endereços necessários** (estações + gateway + rede + broadcast): *(preencher)*
- **Bits de host necessários (n):** *(preencher)*
- **Máscara de sub-rede:** *(decimal)* / *(CIDR)*
- **Tamanho do bloco (2ⁿ):** *(preencher)*

#### Vendas (20 estações)

- **Total de endereços necessários** (estações + gateway + rede + broadcast): *(preencher)*
- **Bits de host necessários (n):** *(preencher)*
- **Máscara de sub-rede:** *(decimal)* / *(CIDR)*
- **Tamanho do bloco (2ⁿ):** *(preencher)*

#### RH (5 estações)

- **Total de endereços necessários** (estações + gateway + rede + broadcast): *(preencher)*
- **Bits de host necessários (n):** *(preencher)*
- **Máscara de sub-rede:** *(decimal)* / *(CIDR)*
- **Tamanho do bloco (2ⁿ):** *(preencher)*

#### Marketing (5 estações)

- **Total de endereços necessários** (estações + gateway + rede + broadcast): *(preencher)*
- **Bits de host necessários (n):** *(preencher)*
- **Máscara de sub-rede:** *(decimal)* / *(CIDR)*
- **Tamanho do bloco (2ⁿ):** *(preencher)*

#### Gerência (2 estações)

- **Total de endereços necessários** (estações + gateway + rede + broadcast): *(preencher)*
- **Bits de host necessários (n):** *(preencher)*
- **Máscara de sub-rede:** *(decimal)* / *(CIDR)*
- **Tamanho do bloco (2ⁿ):** *(preencher)*

### B2. Tabela de Planejamento de Sub-Redes — VLSM (Etapa 2)

Distribua as sub-redes sequencialmente a partir de `200.221.30.0`, utilizando a **máscara mais específica** para cada setor:

| Setor | Estações | Máscara de Sub-Rede | CIDR | End. de Rede | Primeiro IP Utilizável | Último IP Utilizável | End. de Broadcast |
|---|---|---|---|---|---|---|---|
| Produção | 25 | | | | | | |
| Vendas | 20 | | | | | | |
| RH | 5 | | | | | | |
| Marketing | 5 | | | | | | |
| Gerência | 2 | | | | | | |

### B3. Verificação — VLSM (Etapa 3)

#### B3.1 Nenhuma sub-rede se sobrepõe a outra?

*(Responda aqui. Demonstre que os blocos são contíguos e sem conflito.)*

#### B3.2 Cada sub-rede comporta todos os hosts necessários?

*(Responda aqui. Considere estações + gateway.)*

#### B3.3 Todos os endereços estão dentro da faixa `200.221.30.0/24`?

*(Responda aqui. Indique qual é o último endereço de broadcast alocado.)*

#### B3.4 Quantos endereços ficaram sem uso?

*(Responda aqui. Calcule: 256 − total de endereços alocados.)*

---

## Comparação FLSM × VLSM (Etapa 4)

Preencha a tabela abaixo com os totais obtidos em cada caminho:

| Métrica | FLSM | VLSM |
|---------|------|------|
| Máscara(s) utilizada(s) | | |
| Total de endereços alocados | | |
| Total de endereços sem uso (fora das sub-redes) | | |
| Total de endereços desperdiçados (dentro das sub-redes) | | |

---

## Questões para Reflexão

### Questão 1

**Com base na tabela comparativa, explique por que o VLSM é mais eficiente que o FLSM no aproveitamento de endereços IP. Em quais cenários o FLSM ainda poderia ser a melhor escolha?**

*(Responda aqui.)*

### Questão 2

**Considerando a solução VLSM, se a empresa precisasse criar um novo departamento com 10 estações, seria possível acomodá-lo na faixa restante? Justifique indicando a sub-rede que seria utilizada.**

*(Responda aqui.)*

### Questão 3

**Considerando a solução FLSM, seria possível acomodar esse mesmo novo departamento na faixa restante? Compare com a resposta anterior.**

*(Responda aqui.)*

### Questão 4

**Qual é a função do endereço de broadcast em uma sub-rede? Cite um exemplo de protocolo que o utiliza.**

*(Responda aqui.)*

### Questão 5

**Em uma rede real, por que é importante reservar pelo menos um endereço IP para o gateway da sub-rede?**

*(Responda aqui.)*
