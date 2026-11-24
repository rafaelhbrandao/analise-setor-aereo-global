# ✈️ Análise Estratégica do Setor Aéreo Global (2010–2026)

## 📌 Contexto e Objetivo de Negócio
Solução de Business Intelligence desenvolvida para consolidar e analisar indicadores financeiros, operacionais, de frota e de segurança da aviação civil global ao longo do recorte de 2010 a 2026. O projeto permite avaliar a dinâmica de recuperação pós-pandemia, eficiência de malha e rotas, carteira de pedidos dos fabricantes e o histórico de segurança operacional do setor.

---

## 🏗️ Arquitetura e Modelagem de Dados (Star Schema)
O projeto foi estruturado com foco em modelagem dimensional, consistência de filtros e clareza nas regras de negócio:
* **Modelo Dimensional (Star Schema):** Composto por **5 tabelas fato** (`fFinanceiro`, `fPassageiros`, `fRotas`, `fPedidos` e `fIncidentes`) conectadas a **3 dimensões conformadas** (`dAno`, `dRegiao`, `dCompanhia`), garantindo integridade referencial e organização analítica.
* **ETL e Tratamento (Power Query / Linguagem M):** Padronização de nomenclaturas geográficas e corredores aéreos utilizando funções como `Table.TransformColumns` e `List.ReplaceMatchingItems`, além de colunas auxiliares para classificação de fabricantes, reduzindo valores nulos ou inconsistentes nos filtros cruzados.

---

## ⚙️ Regras de Negócio e Soluções em DAX
* **Indicadores de Tráfego:** Cálculo de **RPK** (*Revenue Passenger Kilometers*), **ASK** (*Available Seat Kilometers*) e **Taxa de Ocupação (Load Factor)** com `DIVIDE`, além de métricas de tarifa média e receita/oferta por rota.
* **Medidas Semi-Aditivas (Backlog):** Cálculo da **Carteira de Pedidos** utilizando `CALCULATE` com filtro no último período selecionado (`MAX(dAno[Ano])`), evitando a soma indevida de saldos acumulados ao longo de múltiplos anos.
* **Análise de Segurança:** Consolidação de incidentes, fatalidades totais e média de fatalidades por ocorrência, com recorte por fabricante e tipo de aeronave e detalhamento hierárquico por ano/companhia.

---

## 📊 Estrutura do Relatório (4 Visões Analíticas)
1. **Operações:** Visão financeira e operacional (receita total, lucro operacional, margem média, média de ocupação, evolução anual, lucro por companhia e relação entre tamanho de frota e receita).
2. **Tráfego e Ocupação:** Comparativo histórico entre demanda e capacidade ofertada (*Demanda x Oferecido*), tarifa média e ranking das *Top 10 Rotas*.
3. **Frotas e Pedidos:** Pedidos líquidos, entregas realizadas, taxa de entrega, saldo de *backlog*, série *Entregas x Backlog* e rankings por família de aeronave e fabricante (*Airbus*, *Boeing*, *Embraer*, *COMAC*).
4. **Incidentes:** Histórico anual de ocorrências e fatalidades, ranking de fatalidades por tipo de aeronave e matriz interativa por ano e fabricante.

---

## ⚠️ Premissas, Limitações e Pontos de Atenção
* **Dados parciais em 2026:** A série histórica abrange até 2026 com registros parciais/incompletos no período mais recente da base; quedas observadas no último ponto não devem ser lidas isoladamente como retração consolidada do ano.
* **Leitura visual em gráficos combinados e séries densas:** Algumas visões combinam métricas em escalas distintas ou concentram rótulos próximos em picos/quedas acentuadas (como 2020 ou o fim da série), o que já está mapeado para refinamentos incrementais.

---

## 🤖 Uso de Inteligência Artificial no Desenvolvimento
Este projeto contou com o apoio de Inteligência Artificial como **copiloto técnico** para acelerar discussões de arquitetura, revisar sintaxe/lógica em DAX e Power Query, avaliar alternativas de layout e estruturar a documentação. Todas as decisões de modelagem, regras de negócio, ajustes manuais no Power BI Desktop e validações dos números foram conduzidos e revisados por mim.

---

## 🛠️ Tecnologias Utilizadas
* **Power BI Desktop** (Power Query / Linguagem M, Modelagem Dimensional, DAX e Visualização)
* **GitHub** (Versionamento e documentação técnica)

---

## 🧭 Próximos Passos
* **Evolução do dashboard:** Adicionar navegação customizada entre páginas e continuar refinando o espaçamento de rótulos e títulos de eixos onde houver ganho de leitura.
* **Próximo projeto do portfólio:** Desenvolvimento de um case focado em **Gestão de Ativos** (indicadores como **MTBF**, **MTTR**, **SLA** e ciclo de vida de ativos).