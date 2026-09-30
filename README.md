# SalesInsight PY — Análise de Dados de Vendas

Mini-Projeto Avaliativo do Módulo 01 — Desenvolvimento de IA para Análise Preditiva (SENAI / SCTEC)

## Sobre o projeto

Análise de dados de vendas desenvolvida em Python, usando apenas a biblioteca padrão. O projeto gera um dataset de vendas com dados propositalmente "sujos", carrega, inspeciona, limpa, transforma e agrega esses dados, e exporta um relatório resumido em CSV e JSON.

O cenário: uma empresa de varejo precisa de um relatório analítico para a reunião trimestral da diretoria, respondendo como as vendas se comportam ao longo do tempo, quais produtos, categorias e regiões geram mais receita, quais clientes são mais valiosos e quantas vendas ficaram acima da média.

## O que o projeto analisa

- Receita total, quantidade vendida e número de vendas por mês e por trimestre
- Top 5 produtos por receita
- Receita por categoria
- Receita total e ticket médio por região
- Segmentação de clientes por nível de gasto (Bronze, Prata, Ouro)
- Quantidade de vendas com receita acima da média geral por venda
- Exportação dos resultados em CSV e JSON

## Principais resultados

| Indicador                                 | Resultado                                                                                                     |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Registros brutos → válidos após a limpeza | 200 → 183 (4 datas inválidas e 13 registros com valores ausentes removidos; 15 nomes de cliente padronizados) |
| Receita total                             | R$ 1.290.346,30                                                                                               |
| Receita média por venda                   | R$ 7.051,07                                                                                                   |
| Vendas acima da média                     | 70 de 183                                                                                                     |
| Mês com maior receita                     | Novembro (R$ 160.297,77)                                                                                      |
| Trimestre com maior receita               | Q4 (R$ 375.924,07, 54 vendas)                                                                                 |
| Produto com maior receita                 | Notebook (R$ 374.174,85)                                                                                      |
| Categoria com maior receita               | Celulares (R$ 638.591,77)                                                                                     |
| Região com maior receita                  | Nordeste (R$ 366.321,23, ticket médio de R$ 8.721,93)                                                         |
| Segmentação de clientes                   | 34 Ouro, 10 Prata, 6 Bronze (50 clientes)                                                                     |

## Fluxo do projeto

| Etapa                                       | Requisito | Função                                          |
| ------------------------------------------- | --------- | ----------------------------------------------- |
| Geração do dataset sintético                | RF01      | `gerar_dataset_vendas()`                        |
| Carregamento do CSV                         | RF01      | `carregar_dataset()`                            |
| Inspeção estrutural dos dados               | RF02      | `inspecionar_dados()`                           |
| Limpeza e relatório de limpeza              | RF03      | `limpar_dados()`                                |
| Colunas derivadas                           | RF04      | `criar_colunas_derivadas()`                     |
| Métricas agregadas                          | RF05      | `calcular_metricas()`                           |
| Segmentação de clientes                     | RF06      | `segmentar_clientes()` e `exibir_segmentacao()` |
| Estatísticas gerais (vendas acima da média) | Desafio   | `calcular_estatisticas_gerais()`                |
| Função de ordem superior                    | RF07      | `processar_coluna()`                            |
| Exportação em CSV e JSON                    | RF08      | `exportar_resultados()`                         |
| Fluxo completo de ponta a ponta             | RF09      | `main()`                                        |

## Conceitos aplicados (Módulo 01 — Semanas 01 a 05)

- **Lógica de programação:** variáveis, tipos (`int`, `float`, `str`, `bool`, `list`, `dict`), operadores aritméticos, lógicos e relacionais, `if/elif/else` e laços `for`
- **Estruturas de dados:** listas de dicionários (dataset), dicionário de listas (métricas), tupla no retorno da limpeza, dicionário do relatório de limpeza
- **Funções:** parâmetros, retorno e docstring em todas as funções; funções `lambda` (ordenação, classificação de clientes e transformações); função de ordem superior (`processar_coluna`)
- **Arquivos:** leitura e escrita de CSV (`csv.DictReader` e `csv.DictWriter`) e de JSON (`json.dump` e `json.load`)
- **Módulo `datetime`:** geração de datas, conversão com `strptime` e extração de mês, trimestre e ano
- **Expressões regulares (`re`):** `re.compile()`, `re.sub()` e `re.search()` na padronização dos nomes de cliente
- **Módulos e importação:** `csv`, `json`, `re`, `os`, `random`, `datetime` e `collections`
- **Git e GitHub:** branches por funcionalidade, commits no padrão conventional commits e GitFlow simplificado

## Como executar

O projeto usa apenas a biblioteca padrão do Python. Nenhuma dependência externa precisa ser instalada para o código.

### Google Colab

1. Faça upload do `salesinsight.ipynb` no Colab.
2. Clique em **Ambiente de execução → Executar tudo**.
3. O `vendas.csv` é gerado automaticamente se não existir, e os resultados são gravados na pasta `outputs/`.

### Localmente com VS Code

1. Instale o Python 3.10+ e o VS Code com as extensões **Python** e **Jupyter** (Microsoft).
2. Clone o repositório:
   ```bash
   git clone https://github.com/luiz-camillo/projeto01-sctec-analise-preditiva.git
   cd projeto01-sctec-analise-preditiva
   ```
3. Abra o `salesinsight.ipynb` e selecione um kernel Python (canto superior direito).
4. Na primeira execução, o VS Code pede o pacote `ipykernel`: clique em **Instalar** (ou rode `pip install ipykernel`). Ele é o componente que executa notebooks no VS Code, não uma dependência do projeto.
5. Clique em **Executar Tudo**.

Opcional, com ambiente virtual:

```bash
python -m venv .venv
.venv\Scripts\activate        # Windows
source .venv/bin/activate     # Linux/Mac
pip install ipykernel
```

## Estrutura do projeto

```
projeto01-sctec-analise-preditiva/
|-- README.md
|-- salesinsight.ipynb          # fluxo principal (RF01 a RF09)
|-- vendas.csv                  # dataset sintético gerado pelo próprio notebook
|-- outputs/
|   |-- metricas_por_mes.csv
|   |-- segmentacao_clientes.csv
|   |-- estatisticas_gerais.json
|-- planejamento/
    |-- tarefas-kanban.md
```

## Decisões técnicas

- **Remover registros inválidos em vez de preencher:** registros com data inválida ou sem quantidade/preço são descartados, e o relatório de limpeza mostra quantos saíram por motivo. Preencher valores (imputação) inventaria vendas que não aconteceram e distorceria as métricas.
- **Padronizar o nome do cliente com regex:** nomes como `cliente#016`, `CLIENTE-016` e `Cliente_008!!` são reconstruídos no formato `Cliente_NNN`. Sem isso, o mesmo cliente seria contado como vários, e a segmentação mostraria 58 clientes em vez de 50.
- **Limpar uma cópia de cada registro:** `limpar_dados()` trabalha em cópias, sem alterar a lista original. Assim a célula pode ser executada mais de uma vez sem erro.
- **Acumular métricas em dicionários:** `defaultdict` e `dict.get()` somam receita, quantidade e vendas em uma única passada pelos dados, em vez de recalcular para cada mês, produto ou região.
- **Dataset reproduzível:** o gerador usa `seed=42`, então qualquer pessoa obtém exatamente o mesmo dataset. Ele só é gerado se `vendas.csv` ainda não existir.
- **Caminhos relativos:** todos os arquivos são lidos e gravados com caminhos relativos à pasta do notebook, o que permite rodar tanto no VS Code quanto no Colab.

## Oportunidades de melhoria

- Exibir o nome do mês nas tabelas de métricas, em vez do número
- Adicionar gráficos quando Matplotlib e Seaborn forem trabalhados (Semanas 06 a 08)
- Reescrever o fluxo com Pandas para comparar desempenho e legibilidade
- Criar testes automatizados para as funções de limpeza

## Organização do squad

| Integrante                     | Responsabilidade                                                                    |
| ------------------------------ | ----------------------------------------------------------------------------------- |
| Eduardo                        | RF01 (geração e carregamento do dataset), RF02 (inspeção) e RF03 (limpeza)          |
| Leandro                        | RF04 (colunas derivadas), RF05 (métricas agregadas) e RF09 (fluxo principal)        |
| Luiz Fernando Camillo Ferreira | RF06 (segmentação de clientes), RF07 (função de ordem superior) e RF08 (exportação) |

### Branches

| Branch                       | Conteúdo                       |
| ---------------------------- | ------------------------------ |
| `main`                       | Versão final entregue          |
| `develop`                    | Integração das funcionalidades |
| `feat/leitura-limpeza`       | RF01, RF02 e RF03              |
| `feat/analise-metricas`      | RF04 e RF05                    |
| `feat/metricas-segmentacao`  | RF06                           |
| `feat/exportacao-resultados` | RF07, RF08 e RF09              |
| `docs/readme-video`          | README e vídeo de demonstração |

As tarefas foram organizadas em um quadro Kanban, disponível em [`planejamento/tarefas-kanban.md`](planejamento/tarefas-kanban.md).

## Ferramentas utilizadas

- Python 3.10+
- VS Code (extensões Python e Jupyter) e Google Colab
- Biblioteca padrão do Python: `csv`, `json`, `re`, `datetime`, `os`, `random`, `collections`
- Git e GitHub para versionamento

## Vídeo de demonstração

https://drive.google.com/file/d/1roTKOSzXlyK-AC9q0zGRCvqGMSUoXWbu/view?usp=sharing
