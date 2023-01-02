# Trigger

### O que é, para que serve, quando e como usar?

---
```
Essa é uma pequena documentação sobre triggers, que é um assunto que eu não conhecia muito bem, mas que me ajudou bastante no meu trabalho.

Espero que possa ajudar mais pessoas que estão começando a trabalhar com banco de dados.
```
---

## O que é uma trigger?

Com o passar do tempo, as aplicações foram ficando mais complexas e com isso, a necessidade de automatizar tarefas que antes eram feitas manualmente, aumentou. Para isso, surgiram as triggers, que são funções que são executadas automaticamente quando uma ação é realizada no banco de dados.

Trigger em português significa gatilho, e é exatamente isso que ela faz, ela é acionada quando um evento acontece no banco de dados.

Tendo como exemplo um banco de dados de uma loja, podemos ter uma trigger que é acionada quando um produto é inserido no banco de dados, e que faz com que o estoque seja atualizado automaticamente.


## Para que serve?

As triggers são muito úteis para automatizar tarefas que são realizadas com frequência, e que podem ser feitas de forma mais rápida e eficiente com o uso de triggers.

Como dito anteriormente, podemos ter uma trigger que atualiza o estoque de um produto quando ele é inserido no banco de dados, ou uma trigger que atualiza um log de alterações quando um registro é alterado.

Existem diversas outras aplicações para as triggers, e é importante que você entenda como elas funcionam para que possa utilizá-las da melhor forma possível.

## Como uma trigger funciona?

Uma trigger é composta por três partes:

* **Evento:** é o evento que aciona a trigger, como por exemplo, a inserção de um registro em uma tabela.

* **Momento:** é o momento em que a trigger é executada, como por exemplo, antes ou depois da ação que acionou a trigger.

* **Ação:** é a ação que a trigger executa, como por exemplo, atualizar um registro em outra tabela.

Para ficar mais claro, vamos ver um exemplo de uma trigger que atualiza o estoque de um produto quando ele é inserido no banco de dados.

```sql

CREATE TRIGGER trigger_name AFTER INSERT ON table_name FOR EACH ROW

BEGIN

UPDATE product SET stock = stock + 1 WHERE id = NEW.id;

END;

```

Nesse exemplo, temos uma trigger chamada trigger_name, que é executada depois que um registro é inserido na tabela table_name, e que atualiza o estoque do produto que foi inserido.

Esse é um exemplo bem simples, mas que mostra como uma trigger funciona.

Vamos separar cada parte da trigger para entender melhor como ela funciona.

### Evento

O evento é o que aciona a trigger, e é definido na cláusula ON.

```sql

ON table_name

```

Nesse exemplo, a trigger é acionada quando um registro é inserido na tabela table_name.

### Momento

O momento é o momento em que a trigger é executada, e é definido na cláusula AFTER.

```sql

AFTER INSERT

```

Nesse exemplo, a trigger é executada depois que um registro é inserido na tabela table_name.

Existem outros momentos que podem ser utilizados, como por exemplo, BEFORE, que é executado antes da ação que acionou a trigger.

### Ação

A ação é a ação que a trigger executa, e é definida no bloco BEGIN e END.

```sql

BEGIN

UPDATE product SET stock = stock + 1 WHERE id = NEW.id;

END;

```

Nesse exemplo, a trigger atualiza o estoque do produto que foi inserido na tabela table_name.

### FOR EACH ROW

A cláusula FOR EACH ROW é utilizada para que a trigger seja executada para cada registro que é inserido na tabela.

```sql

FOR EACH ROW

```

Nesse exemplo, a trigger é executada para cada registro que é inserido na tabela table_name.

### OLD e NEW

As variáveis OLD e NEW são utilizadas para acessar os dados do registro que está sendo inserido na tabela.

```sql

UPDATE product SET stock = stock + 1 WHERE id = NEW.id;

```

Nesse exemplo, a trigger atualiza o estoque do produto que está sendo inserido na tabela table_name.

A variável OLD é utilizada para acessar os dados do registro que está sendo alterado, e a variável NEW é utilizada para acessar os dados do registro que está sendo inserido.


## Tipos de trigger

Existem dois tipos de trigger, que são:

* **Trigger de DML:** são triggers que são executadas quando uma ação de DML é realizada no banco de dados, como por exemplo, a inserção de um registro em uma tabela.

* **Trigger de DDL:** são triggers que são executadas quando uma ação de DDL é realizada no banco de dados, como por exemplo, a criação de uma tabela.



## Perfomance

Uma das coisas que você deve ter em mente ao utilizar triggers é a performance, pois elas podem afetar a performance do banco de dados.

Isso acontece porque as triggers são executadas sempre que um evento é acionado, e isso pode ser um problema se o evento for acionado com frequência.

Um exemplo de uma situação em que isso pode acontecer é quando você tem uma tabela de log de alterações, e que toda vez que um registro é alterado, uma trigger é executada para inserir um registro na tabela de log.

Existem algumas formas de melhorar a performance das triggers, como por exemplo, utilizar o momento BEFORE, que é executado antes da ação que acionou a trigger, e que pode ser mais rápido que o momento AFTER, mas isso depende muito do que a trigger faz.

Outra forma de melhorar a performance é utilizar a cláusula FOR EACH ROW, que faz com que a trigger seja executada para cada registro que é afetado pela ação que acionou a trigger, e não uma única vez para todos os registros.

## Conclusão

Espero que esse artigo tenha ajudado você a entender melhor o que são triggers, e como elas funcionam.

Caso você tenha alguma dúvida, deixe um comentário que eu responderei o mais rápido possível.

Qualquer correção ou sugestão, deixe também nos comentários.

