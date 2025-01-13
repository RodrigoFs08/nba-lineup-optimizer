# Otimizador de Times NBA usando Algoritmos Genéticos

## 📝 Descrição do Projeto

Este projeto implementa um algoritmo genético para otimizar a seleção de times titulares da NBA, considerando múltiplas métricas de desempenho e restrições orçamentárias. O sistema analisa dados históricos das últimas três temporadas da NBA para encontrar as melhores combinações possíveis de jogadores que maximizam o desempenho da equipe dentro das limitações do salary cap.

### 🎯 Objetivo

O objetivo principal é desenvolver um sistema de otimização que possa:
- Selecionar os melhores quintetos titulares possíveis dentro do limite salarial
- Maximizar métricas de desempenho ofensivo e defensivo
- Respeitar restrições de posicionamento dos jogadores
- Encontrar o melhor equilíbrio entre diferentes aspectos do jogo

## 🔍 O Problema

O problema de otimização consiste em selecionar 5 jogadores da NBA para formar um time titular, respeitando as seguintes restrições:

1. **Restrições de Posição:**
   - 2 armadores (Guards)
   - 2 alas (Forwards)
   - 1 pivô (Center)

2. **Restrições Orçamentárias:**
   - O salário total não pode ultrapassar 80% do salary cap da NBA
   - Consideração dos salários reais dos jogadores

3. **Métricas de Desempenho:**
   - OBPM (Offensive Box Plus/Minus)
   - DBPM (Defensive Box Plus/Minus)
   - TS% (True Shooting Percentage)
   - AST% (Assist Percentage)
   - USG% (Usage Rate)
   - 3P% (Three-Point Percentage)
   - STL% (Steal Percentage)
   - BLK% (Block Percentage)

## 🧬 Implementação do Algoritmo Genético

### Estrutura do Cromossomo
Cada cromossomo representa um time válido com 5 jogadores, onde cada gene é o ID único de um jogador.

### Função de Fitness
A função de fitness considera múltiplos fatores com diferentes pesos:
- OBPM: 31%
- DBPM: 28%
- TS%: 14%
- 3P%: 8%
- AST%: 5%
- USG%: 5%
- STL%: 5%
- BLK%: 4%

### Operadores Genéticos

1. **Seleção:**
   - Implementação de três métodos:
     - Torneio
     - Roleta
     - Ranking
   - Comparação de eficácia entre os métodos

2. **Crossover:**
   - Ponto único de corte
   - Verificação de validade dos times resultantes
   - Correção automática de combinações inválidas

3. **Mutação:**
   - Taxa de mutação: 10%
   - Substituição aleatória de jogadores
   - Manutenção da validade das posições

### Critérios de Parada

- Número máximo de gerações atingido
- Convergência detectada (sem melhoria significativa)
- Diversidade mínima da população alcançada
- Meta de fitness atingida (quando especificada)

## 📊 Coleta e Processamento de Dados

### Fonte dos Dados
- NBA API para estatísticas das últimas 3 temporadas
- Dados de salários atualizados dos jogadores
- Métricas avançadas de desempenho

### Processamento
- Filtro de jogadores com mais de 50 jogos por temporada
- Normalização de estatísticas
- Tratamento de dados faltantes
- Padronização de nomes e posições

## 🚀 Como Executar o Projeto

### Pré-requisitos
```bash
pip install pandas numpy matplotlib nba_api
```

### Configuração
1. Clone o repositório
2. Instale as dependências
3. Execute o notebook principal

### Execução
```python
# Criar instância do otimizador
optimizer = NBALineupOptimizer(
    players_df=df,
    population_size=1000,
    max_generations=50,
    convergence_generations=10,
    min_diversity=0.01
)

# Executar otimização
best_lineup, best_fitness = optimizer.optimize()
```

## 📈 Resultados e Análises

O sistema permite:
- Visualização da evolução do fitness ao longo das gerações
- Comparação entre diferentes métodos de seleção
- Análise de diversidade da população
- Detalhamento completo dos times otimizados

### Métricas de Avaliação
- Fitness médio e máximo por geração
- Tempo de convergência
- Diversidade populacional
- Qualidade das soluções encontradas

## 🤝 Contribuições

Contribuições são bem-vindas! Para contribuir:
1. Faça um fork do projeto
2. Crie uma branch para sua feature
3. Faça commit das mudanças
4. Faça push para a branch
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.

## ✨ Agradecimentos

- NBA API pela disponibilização dos dados
- Comunidade de análise de dados esportivos
- Professores e colegas que contribuíram com feedback

