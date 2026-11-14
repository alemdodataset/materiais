# Resposta do desafio · ep. 1 · NULL não é zero

**Os vazios de verdade (5):** Caio (célula vazia), Duda (`N/A`), Enzo (`-`), Gabi (um espaço ` `) e Hugo (`não informado`).
O pandas já reconhece sozinho a célula vazia e o `N/A`. Os outros três ele lê como texto, e por isso a coluna vira texto e a média dá erro.

**Os zeros são reais:** Bia e Iara estão desempregadas. Renda zero é uma informação, não um vazio. Apagar esses zeros seria um erro tão grande quanto transformar vazio em zero.

```python
cadastro = pd.read_csv("cadastro_desafio.csv", na_values=["-", "não informado", " "])
cadastro["renda"].isna().sum()   # 5
cadastro["renda"].mean()         # 2020.0 -> média de quem informou (5 pessoas)
```

**Compare:**
| Escolha | Média |
|---|---|
| Só quem informou (certo) | R$ 2.020 |
| Vazio virou zero | R$ 1.010 |
| Zero virou vazio (apagou as desempregadas) | R$ 3.366,67 |

A mesma tabela, três respostas. A diferença é só o que você decidiu que o vazio significa.

> Cuidado: alguns editores apagam o espaço no fim da linha da Gabi. Se isso acontecer, ela vira uma célula vazia comum.
