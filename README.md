# Exercícios de Pandas: groupby com preços Apple

Exercícios de `groupby` do curso de Pandas da Jornada de dados, feitos com uma base de preços de produtos Apple (2020 a 2026) vendidos na Amazon e no Flipkart.

## O que tem aqui

Tudo está em [`notebooks/groupby_apple.ipynb`](notebooks/groupby_apple.ipynb), em 3 níveis:

- **Nível 1, agregar e agrupar:** média, mediana, máximo e mínimo de uma coluna; loop x `groupby`; `.count()` x `.size()`.
- **Nível 2, as formas do resultado:** duas chaves, `.reset_index()`, várias colunas de valor, `.agg` com nomes, contas entre resultados (percentual de esgotados).
- **Nível 3, desafio final:** "os eventos de venda dão desconto de verdade?", com tratamento de valores vazios (`fillna`), comparação por evento e categoria, e um olho crítico sobre produtos recondicionados. Termina com um bônus de `transform`.

## Base de dados

`data/apple_products_pricing_2020_2026.csv`: 80.000 anúncios, com plataforma, categoria (Mac, Watch, iPad, iPhone), modelo, condição (novo ou recondicionado), preço de lançamento e atual, desconto, evento de venda e status de estoque.

## Principais achados

- **Preço atual médio:** Mac US$ 1.382,49; iPhone US$ 758,67; iPad US$ 573,08; Watch US$ 398,64.
- **Queda de valor:** o Mac perde mais em dólares (US$ 229,82), mas o Watch perde mais em proporção (25,3%).
- **Plataforma:** Amazon e Flipkart têm preços médios quase iguais por categoria (diferença menor que 2%).
- **Estoque:** o iPad é a categoria que mais esgota (19,8% dos anúncios).
- **Eventos de venda:** só 6.649 dos 80.000 anúncios estão em evento. Todos os eventos têm desconto médio maior que os anúncios fora de evento (20,3%): de 11,2 pontos percentuais (Black Friday) a 16,7 (Big Billion Days).
- **Olho crítico:** a proporção de recondicionados é praticamente igual em todos os eventos (cerca de 25%). Refazendo a comparação só com produtos novos, a conclusão se mantém (de 11,9 a 17,5 pontos).
- **Maior desconto médio por combinação:** iPhone na Big Billion Days, com 39,9%.
- **Bônus:** os 5 anúncios mais acima da média da própria categoria são todos MacBook Pro 14", cerca de US$ 656 acima da média do Mac.

Todos os números são médias, que misturam modelos e datas.

## Como rodar

O ambiente é gerenciado com [uv](https://docs.astral.sh/uv/):

```bash
uv sync
```

Depois abra o notebook no VS Code (ou Jupyter) com o kernel do ambiente `.venv`. O notebook lê o CSV de `../data/`.
