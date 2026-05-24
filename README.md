# 🍷 Data Pipeline para Análise de Vinhos

## Visão Geral

Este projeto demonstra a implementação de um **pipeline de dados robusto e escalável** para ingestão, transformação e orquestração de dados de vinhos utilizando **Apache Hop**, uma plataforma open-source de engenharia de dados, integração e orquestração mantida pela Apache Software Foundation.

O pipeline processa dados de vinhos de diferentes países, aplicando transformações sofisticadas e gerando relatórios agregados e ordenados para análise especializada.

---

## 🎯 Objetivo do Projeto

Automatizar a ingestão de dados de vinhos em formato CSV e executar uma série de transformações complexas que segmentam os dados por país, aplicam filtros específicos e geram arquivos processados prontos para análise.

---

## 📊 Arquitetura do Pipeline

### Fluxo de Processamento

```
Input CSV → Transformação de Dados → Filtragem → Orquestração Segmentada
```

O pipeline está dividido em duas sub-pipelines principais que processam dados de **Itália (IT)** e **França (FR)** de formas distintas:

### **1️⃣ Etapa de Ingestão**
- **Input CSV**: Importação de dados de vinhos em formato CSV

### **2️⃣ Etapa de Transformação e Tratamento**
- **Tratamento de Dados**: Normalização de códigos de países
  - `France` → `FR`
  - `Italy` → `IT`

### **3️⃣ Etapa de Filtragem**
- **Filter Rows**: Remove registros que não atendem aos critérios de país (IT ou FR)
- Dados inválidos são descartados automaticamente

### **4️⃣ Etapa de Orquestração (Segmentada)**

#### **Fluxo para Itália (IT)** ✅
- Os dados italianos são exportados diretamente em arquivo `.txt` formatado
- Saída: `arquivo_saida_vinhos_IT.txt`

#### **Fluxo para França (FR)** 🇫🇷
1. **Seleção de Campos**: Extração dos campos relevantes
   - `country` (País)
   - `province` (Província)
   - `price` (Preço)
   - `points` (Pontos)

2. **Primeira Ordenação**: Ordenação inicial por preço e pontos (ordem ascendente)

3. **Agregação por Localidade**: Agrupamento por país e província com cálculos:
   - Soma de preços
   - Soma de pontos

4. **Segunda Ordenação**: Reordenação final dos dados agregados por preço e pontos

5. **Exportação**: Geração de arquivo processado e pronto para análise
   - Saída: `arquivo_franca_agregado_e_ordenado.txt`

---

## 📁 Estrutura de Arquivos

```
Data-Pipeline-for-wines/
└── outputs/             # Configuração do Apache Hop
    └── arquivo_saida_vinhos_IT.txt   # Dados brutos de vinhos italianos
    └── arquivo_franca_agregado_e_ordenado.txt  #Dados franceses agregados por região e ordenados
├── README.md                    # Documentação do projeto
├── pipeline.png                 # Visualização da arquitetura
├── vinhos_mundo.csv             # Fonte de dados
└── pipeline_config/             # Configuração do Apache Hop
    └── wine_data_pipeline.hpl   # Definição da pipeline
```

---

## 🚀 Tecnologias Utilizadas

- **Apache Hop**: Plataforma de orquestração de dados open-source
- **CSV**: Formato de entrada de dados
- **TXT**: Formato de saída processada

---

## 💡 Funcionalidades Principais

✔️ Ingestão automatizada de dados  
✔️ Normalização de códigos de país  
✔️ Filtragem inteligente de registros  
✔️ Processamento segmentado por país  
✔️ Agregação e análise de dados  
✔️ Geração de relatórios formatados  
✔️ Orquestração escalável e mantenível  

---

## 📈 Casos de Uso

- **Análise Comparativa**: Comparar características de vinhos italianos e franceses
- **Relatórios Agregados**: Gerar sumários de preços e avaliações por região
- **Data Warehousing**: Alimentar sistemas de BI com dados processados
- **Automação ETL**: Executar transformações repetitivas sem intervenção manual

---

## 🔧 Como Executar

1. Instalar Apache Hop (versão 2.0 ou superior)
2. Clonar este repositório
3. Importar a pipeline no Apache Hop
4. Configurar a origem CSV com seus dados
5. Executar a pipeline

---

## 📝 Saídas Esperadas

| Arquivo | Descrição | Formato |
|---------|-----------|---------|
| `arquivo_saida_vinhos_IT.txt` | Dados brutos de vinhos italianos | TXT |
| `arquivo_franca_agregado_e_ordenado.txt` | Dados franceses agregados por região e ordenados | TXT |

---

## 👨‍💻 Autor

Cristiano Jacinto da Gama 
Projeto desenvolvido como exemplo de implementação de pipeline de dados com Apache Hop.

---

## 📄 Licença

Este projeto é licenciado sob a mesma licença do Apache Hop.

---

## 🤝 Contribuições

Contribuições são bem-vindas! Sinta-se livre para abrir issues ou pull requests.
