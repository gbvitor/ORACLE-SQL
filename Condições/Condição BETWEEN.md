### Condição BETWEEN.

Uma condição BETWEEN determina se o valor de uma expressão está em um intervalo definido por duas outras expressões.

O valor de

```sql
expr1 NOT BETWEEN expr2 AND expr3
```

é o valor da expressão

```sql
NOT (expr1 BETWEEN expr2 AND expr3)
```

E o valor de

```sql
expr1 BETWEEN expr2 AND expr3
```

é o valor da expressão booleana:

```sql
expr2 <= expr1 AND expr1 <= expr3
```

Se expr3 < expr2, o intervalo estará vazio. Se expr1 for NULL, então o resultado é FALSE. Se expr1 não for NULL, então o valor está no caso comum e quando a palavra-chave é usada.

O operador booleano AND pode produzir resultados inesperados. Especificamente, na expressão x AND yx IS NULL, a condição não é suficiente para determinar o valor da expressão. O segundo operando ainda deve ser avaliado. O resultado é se o segundo operando tiver o valor FALSE e caso contrário. Consulte Condições lógicas para obter mais informações sobre FALSE, NULL, AND.

| **Tipo de condiçáo**  |                             **Operação**                             | **Exemplo**                                                                                   |
| :-------------------: | :------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------- |
| [NOT] BETWEEN X AND Y | [NOT] (expr2 menor ou igual a expr1 expr1 menor ou igual a expr3AND) | SELECT \* <br>FROM employees <br>WHERE salary BETWEEN 2000 AND 3000 <br>ORDER BY employee_id; |
