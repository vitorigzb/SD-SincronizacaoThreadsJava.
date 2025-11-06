# 🧩 Análise de Sincronização em Threads Java

Este relatório apresenta uma análise técnica e comparativa das três atividades práticas do projeto **SD-SincronizacaoThreadsJava**, abordando diferentes formas de sincronização entre threads em Java.

---

## ⚙️ Atividade Prática 01 — Sem Sincronização

### 💻 Análise técnica da execução
Mesmo rodando o mesmo programa duas vezes, as saídas foram um pouco diferentes, em alguns momentos, o consumidor leu valores repetidos e aordem de execução entre os dois mudaram entre um log e outro.
Isso aconteceu porque não há sincronização no código, as duas threads acessam e mudam a váriavel ao mesmo tempo, sem nenhuma forma de controle, o produtor tenta armazenar um novo valor em Dado, e o Consumidor tenta ler o mesmo valor várias vezes ao mesmo tempo.
Esse tipo de comportamento mostra claramente a condição de corrida ou a famosa race condition, no caso aqui é quando  o resultado depende da ordem de execução das threads, algo que não conseguimos prever.

O programa funciona, mas é instável e inconsistente.  
Cada execução gera um resultado diferente, o que comprova que sem sincronização, não há garantia de integridade dos dados.  

**Exemplo de saída:**

Consumidor: 0
Produtor: 0
Produtor: 1
Produtor: 2
Consumidor: 2
Consumidor: 2
Consumidor: 2
Produtor: 3
Consumidor: 3
Consumidor: 3 

## 🧱 Atividade Prática 02 — Sincronização com Monitores

### 💻 Análise técnica da execução
Usando a sincronização com monitores, múltiplas threads são impedidas de serem criadas ao mesmo tempo, o que garante que cada thread termine suas tarefas uma de cada vez.
Sem a sincronização, ocorre dados quebrados, os resultados variam.

Ou seja usando a sincronização, protegemos dados , temos uma execução estável e consistente, enquanto sem a sincronização, recebemos a possibilidade de dados corrompidos, como o consumo de dados repetidos ou errados.

**Exemplo de saída:**

Armazenar Iniciando...
Armazenar Finalizando...
Carregar Iniciando...
Carregar Finalizando...
Consumidor usando Monitor: 0
Produtor usando Monitor: 0
Armazenar Iniciando...
Armazenar Finalizando...
Produtor usando Monitor: 1

## 🔔 Atividade Prática 03 — Sincronização com Eventos (`wait()` / `notify()`)

### 💻 Análise técnica da execução
Sem sincronização de dados, temos desordem e muitos erros, com a sincronização com monitores, múltiplas threads são impedidas de serem criadas ao mesmo tempo, garante exclusão mútua, porém não há uma coordenação direta, e agora com a sincronização com eventos, conseguimos o equilibrio ideal, produtor e consumidor trabalham em harmonia, alternando corretamente o que garante resultados consistentes.

  Ou seja, a sincronização com eventos é a **abordagem mais eficiente e refinada**:
- Garante a integridade dos dados  
- Elimina as condições de corrida  
- Estabelece comunicação direta entre as threads  
- Melhora o desempenho geral

## 💬 Opinião Pessoal  

Durante a análise, ficou claro que a **sincronização é essencial** para o funcionamento correto de sistemas com múltiplas threads.  
A ausência dela causa resultados imprevisíveis e inconsistentes.  
A sincronização com monitores traz segurança, mas é a **sincronização com eventos** que realmente mostra a força da comunicação entre threads, permitindo que produtor e consumidor cooperem de forma eficiente.

---

✍️ **Autor:** *[Vitoria Gabriely Lacerda]*  
📅 **Data:** *[12 de nov]*  
📘 **Disciplina:** Sistemas Distribuídos — *Sincronização de Threads em Java*
