# ✈️ Análise Estratégica do Setor Aéreo Global (2010–2026)

## 📌 Contexto e Objetivo de Negócio
Solução de Business Intelligence desenvolvida para consolidar e analisar indicadores financeiros, operacionais, de frota e de segurança da aviação civil global ao longo de 17 anos (2010–2026). O projeto permite avaliar a dinâmica de recuperação pós-pandemia, eficiência de rotas, carteira de pedidos dos fabricantes e o histórico de segurança do setor.

---

## 🏗️ Arquitetura e Modelagem de Dados (Star Schema)
O projeto foi estruturado seguindo as melhores práticas de modelagem dimensional e qualidade de dados:
* **Modelo Dimensional (Star Schema):** Composto por **5 tabelas fato** no centro (Finanças, Passageiros, Rotas, Pedidos e Segurança) conectadas a **3 dimensões conformadas** (`dAno`, `dRegiao`, `dCompanhia`), garantindo integridade referencial e alta performance nas consultas.
* **ETL e Tratamento (Power Query / Linguagem M):** Padronização de nomenclaturas geográficas e corredores aéreos utilizando funções como `Table.TransformColumns` e `List.ReplaceMatchingItems`, eliminando valores nulos ou inconsistentes nos filtros cruzados.

---

## ⚙️ Regras de Negócio e Soluções em DAX
* **Indicadores de Tráfego:** Implementação dos cálculos de **RPK** (*Revenue Passenger Kilometers*) e **ASK** (*Available Seat Kilometers*), utilizando divisões ponderadas (`DIVIDE`) para extrair a **Taxa de Ocupação (Load Factor)** real da malha aérea.
* **Medidas Semi-Aditivas (Backlog):** Tratamento da **Carteira de Pedidos** utilizando `CALCULATE` com filtro dinâmico no último período selecionado (`MAX(dAno[Ano])`), evitando a soma indevida de saldos acumulados ao longo dos anos.
* **Análise de Segurança:** Cruzamento de incidentes e fatalidades por fabricante e modelo de aeronave, com drill-down interativo até o nível do voo e descrição da ocorrência.

---

## 📊 Estrutura do Relatório (4 Visões Analíticas)
1. **Operações (Visão Executiva):** Saúde financeira global (receita, lucro operacional, margem e tamanho médio de frota).
2. **Tráfego e Ocupação:** Evolução histórica de demanda vs. capacidade ofertada, tarifa média e ranking das Top 10 rotas globais.
3. **Frota e Pedidos:** Dinâmica de pedidos líquidos, entregas realizadas, saldo de backlog e participação de mercado por fabricante (Airbus, Boeing, Embraer, COMAC).
4. **Segurança Aérea:** Histórico de ocorrências e fatalidades, com matriz analítica detalhada por companhia e aeronave.

---

## 🚀 Tecnologias Utilizadas
* **Power BI Desktop** (Modelagem, DAX, Power Query / ETL)
* **GitHub** (Controle de versão e documentação)