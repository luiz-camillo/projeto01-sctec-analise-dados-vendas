# Kanban — SalesInsight PY

Mapa do projeto e divisão das tarefas do squad.

## Mapa do projeto

Gerar dataset → Carregar → Inspecionar → Limpar → Colunas derivadas → Métricas → Segmentação → Exportação → `main()`

## Responsabilidades

| Requisito | Tarefa                                        | Responsável   | Branch                       |
| --------- | --------------------------------------------- | ------------- | ---------------------------- |
| RF01      | Gerar e carregar o dataset de vendas          | Eduardo       | `feat/leitura-limpeza`       |
| RF02      | Inspecionar e descrever os dados              | Eduardo       | `feat/leitura-limpeza`       |
| RF03      | Limpar e tratar os dados (datetime e regex)   | Eduardo       | `feat/leitura-limpeza`       |
| RF04      | Criar colunas derivadas                       | Leandro       | `feat/analise-metricas`      |
| RF05      | Calcular métricas agregadas                   | Leandro       | `feat/analise-metricas`      |
| RF06      | Segmentar clientes por nível de gasto         | Luiz Fernando | `feat/metricas-segmentacao`  |
| RF07      | Função de ordem superior (`processar_coluna`) | Luiz Fernando | `feat/exportacao-resultados` |
| RF08      | Exportar resultados em CSV e JSON             | Luiz Fernando | `feat/exportacao-resultados` |
| RF09      | Fluxo completo com `main()`                   | Leandro       | `feat/exportacao-resultados` |
| —         | README e vídeo de demonstração                | Squad         | `docs/readme-video`          |
