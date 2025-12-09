# 🏦 Sistema Bancário com SQL e Analytics

Sistema bancário completo desenvolvido em PostgreSQL com análises avançadas, dashboards e relatórios executivos.

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)

## 📋 Índice

- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Estrutura do Banco](#estrutura-do-banco)
- [Como Usar](#como-usar)
- [Queries de Exemplo](#queries-de-exemplo)
- [Analytics](#analytics)


## 🎯 Sobre o Projeto

Este projeto implementa um sistema bancário completo com:
- Gerenciamento de clientes, contas e transações
- Sistema de empréstimos e cartões
- Analytics avançado (CLV, Churn Rate, RFM)
- Dashboards e KPIs
- Relatórios executivos

## ✨ Funcionalidades

### Sistema Base
- ✅ Cadastro de clientes
- ✅ Gerenciamento de contas (Corrente, Poupança, Universitária, Premium)
- ✅ Transações (Depósito, Saque, Transferência, PIX, TED, DOC)
- ✅ Cartões de débito e crédito
- ✅ Sistema de empréstimos
- ✅ Histórico completo de transações

### Analytics
- 📊 Dashboard geral do banco
- 📈 Análise de transações (por tipo, dia, hora)
- 👥 Top clientes por saldo e atividade
- 🗺️ Distribuição geográfica
- 💰 CLV (Customer Lifetime Value)
- 📉 Churn Rate (taxa de evasão)
- 🎯 Segmentação RFM (Recency, Frequency, Monetary)
- 💳 Análise de empréstimos
- 💵 Receitas por produto

## 🗄️ Estrutura do Banco

### Tabelas Principais
1. **clientes** - Dados dos clientes
2. **contas** - Contas bancárias
3. **transacoes** - Histórico de transações
4. **emprestimos** - Empréstimos concedidos
5. **cartoes** - Cartões de débito e crédito
6. **tipos_conta** - Tipos de conta disponíveis
7. **tipos_transacao** - Tipos de transação

### Diagrama ER
```
clientes (1) ──── (N) contas (1) ──── (N) transacoes
                       │
                       ├──── (N) cartoes
                       └──── (N) emprestimos
```

## 🚀 Como Usar

### Pré-requisitos
- PostgreSQL 12+
- Cliente SQL (psql, pgAdmin, DBeaver, ou VS Code com SQLTools)

### Instalação

1. **Clone o repositório**
```bash
git clone https://github.com/seu-usuario/sistema-bancario-sql.git
cd sistema-bancario-sql
```

2. **Crie o banco de dados**
```bash
createdb banco_sistema
```

3. **Execute o script de instalação**
```bash
psql -d banco_sistema -f 01-instalacao/sistema_bancario_completo.sql
```

4. **Execute o sistema de analytics**
```bash
psql -d banco_sistema -f 02-analytics/sistema_analytics_bancario.sql
```

5. **Aplique as correções (opcional)**
```bash
psql -d banco_sistema -f 03-correcoes/corrigir_todos_nulls.sql
```

## 📝 Queries de Exemplo

### Dashboard Geral
```sql
SELECT * FROM public.dashboard_geral;
```

### Top 10 Clientes
```sql
SELECT * FROM public.top_clientes_saldo LIMIT 10;
```

### Transações da Semana
```sql
SELECT * FROM public.view_extrato_completo
WHERE data_transacao >= CURRENT_DATE - INTERVAL '7 days'
ORDER BY data_transacao DESC;
```

### Realizar Transferência
```sql
SELECT public.realizar_transferencia(
    '0001-12345-6',  -- conta origem
    '0001-23456-7',  -- conta destino
    100.00,          -- valor
    'Pagamento'      -- descrição
);
```

### Segmentação de Clientes
```sql
SELECT * FROM public.segmentar_clientes();
```

## 📊 Analytics

### KPIs Principais
- CAC (Custo de Aquisição de Cliente)
- LTV (Lifetime Value)
- Churn Rate
- Taxa de Conversão
- Taxa de Inadimplência
- Ticket Médio

### Análises Disponíveis
- Performance por estado
- Análise de faixa etária
- Crescimento mensal
- Análise de retenção por coorte
- Tendências de transações
- Top dias com maior volume


## 🔧 Funções Principais

### `realizar_transferencia(origem, destino, valor, descricao)`
Realiza transferência entre contas com validações.

### `consultar_saldo(numero_conta)`
Consulta saldo e informações da conta.

### `calcular_clv(id_cliente)`
Calcula o Customer Lifetime Value do cliente.

### `segmentar_clientes()`
Segmenta clientes usando análise RFM.

### `calcular_churn_rate(meses)`
Calcula taxa de evasão de clientes.

### `analise_periodo_customizado(data_inicio, data_fim)`
Análise de transações em período específico.

## 📈 Exemplos de Análises

### Clientes com Alto Valor em Risco
```sql
SELECT * FROM public.segmentar_clientes()
WHERE segmento IN ('VIP', 'Premium') 
AND recency_days > 60;
```

### Performance Mensal
```sql
SELECT * FROM public.relatorio_executivo_mensal(
    EXTRACT(MONTH FROM CURRENT_DATE)::INT,
    EXTRACT(YEAR FROM CURRENT_DATE)::INT
);
```

### Comparação Mês Atual vs Anterior
```sql
SELECT * FROM public.comparacao_mensal();
```


## 📝 To-Do

- [ ] Dashboard web com React
- [ ] API REST com Node.js/Python
- [ ] Sistema de notificações
- [ ] Integração com Power BI
- [ ] Sistema de investimentos
- [ ] Autenticação e segurança
- [ ] Testes automatizados

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.




Desenvolvido como projeto educacional de SQL e Analytics.
