
# Cryptocurrency Market Sentiment Analysis | AWS Cloud

## Parallel Financial Intelligence: Bitcoin, Monero and Google Search Sentiment

An end-to-end AWS cloud project investigating the relationship between online search interest and cryptocurrency market performance through the **parallel analysis of Bitcoin (BTC) and Monero (XMR)**.

The project combines two complementary dimensions: a comparative financial investigation of how online attention relates to asset prices, and the development of a scalable cloud architecture capable of executing independent financial data processing pipelines simultaneously.

Rather than analyzing a single relationship between market sentiment and asset performance, the project examines **two distinct sentiment–price relationships**:

- **Bitcoin:** historical BTC prices and Bitcoin-related Google search interest.
- **Monero:** historical XMR prices and Monero-related Google search interest.

Both analyses cover the 2019–2024 period and follow a consistent methodology, enabling the observed relationships to be interpreted comparatively.

The underlying infrastructure integrates **Amazon S3, AWS Glue ETL, Apache Spark/PySpark, AWS Step Functions, Amazon Redshift and Amazon QuickSight**.

The project's central achievement is the combination of **dual-asset financial intelligence and parallel cloud orchestration**, creating a reproducible analytical framework that can be extended to additional financial instruments and external market indicators.

## 1. Project Objectives and Financial Research Questions

Cryptocurrency prices are influenced by a complex interaction of investor expectations, market liquidity, macroeconomic conditions, regulatory developments and collective market behavior.

Online search activity offers an additional perspective on market attention. Changes in the volume of cryptocurrency-related searches may coincide with significant price movements, precede changes in market conditions or reflect investor reactions to movements already underway.

This project investigates whether the relationship between online attention and market prices can be observed consistently across different cryptocurrencies.

The analysis addresses three interconnected questions:

1. **Financial relationship:** How does Google search interest evolve in relation to cryptocurrency prices, and how does this relationship change across market conditions?
2. **Cross-asset comparison:** Does the association between online attention and market performance display similar characteristics for Bitcoin and Monero, or are there meaningful differences between the two assets?
3. **Technological scalability:** How can a cloud architecture automate and execute these analyses in parallel while preserving consistent data structures and analytical methodologies?

The project therefore extends beyond a single-asset market sentiment study.

By replicating the analysis across two distinct cryptocurrencies, it provides a broader perspective on the potential relevance of online attention as an explanatory market indicator.

The financial investigation is exploratory: the documented results identify visual relationships and temporal patterns, rather than establishing statistical causality or independently validated predictive performance.

## 2. The Analytical Contribution: Two Assets, Two Sentiment Indicators

### A Dual-Asset Financial Intelligence Framework

The most important analytical characteristic of the project is its comparative design.

For each cryptocurrency, the historical market price series is integrated with a dedicated Google Trends search-interest indicator.

This creates two independent but methodologically comparable datasets.

| Analytical Dimension | Bitcoin (BTC) | Monero (XMR) |
|---|---|---|
| Financial asset | Bitcoin | Monero |
| Market variable | Historical price | Historical price |
| External indicator | Bitcoin Google search interest | Monero Google search interest |
| Historical period | 2019–2024 | 2019–2024 |
| Analytical frequency | Weekly | Weekly |
| Final analysis | Price vs. online attention | Price vs. online attention |
| Visualization | Amazon QuickSight | Amazon QuickSight |

The approach makes it possible to examine the relationship between investor attention and market performance within each asset and then compare the observed behavior.

This is particularly valuable because Bitcoin and Monero represent different cryptocurrency market segments.

Bitcoin is characterized by broad market recognition and substantial investor participation, while Monero operates within a more specialized cryptocurrency segment.

Applying the same analytical framework to both assets provides an opportunity to investigate whether the relationship between online interest and prices appears specific to a particular cryptocurrency or can also be observed in a different market context.

### Why the Comparative Dimension Matters

A single-asset analysis may reveal an association between Google search interest and market prices, but it cannot establish whether that association is specific to the asset being examined.

Introducing a second cryptocurrency creates an additional analytical reference.

The project can therefore investigate:

- Whether both assets exhibit a visible relationship between search interest and price movements.
- Whether the relationships appear equally consistent over time.
- Whether major market movements coincide with changes in online attention.
- Whether the apparent direction or timing of the relationship changes across historical periods.

The two analyses do not constitute a formal statistical replication test, but they substantially broaden the scope of the exploratory investigation.

**The distinctive contribution is the examination of the same financial question across two independently processed asset–sentiment relationships, within one integrated analytical framework.**

## 3. The Technological Contribution: Parallel AWS Orchestration

### From Independent Pipelines to Coordinated Multi-Asset Processing

The project's second major contribution is the design and implementation of an AWS architecture that processes Bitcoin and Monero through separate, coordinated workflows.

Each cryptocurrency requires its own data preparation, transformation and integration processes.

Rather than executing the complete Bitcoin workflow before beginning the Monero workflow, the project uses **AWS Step Functions to orchestrate both pipelines in parallel**.

This is a fundamental architectural choice.

Parallel execution allows independent data processing branches to operate concurrently while preserving a centralized orchestration structure.

The result is a cloud environment designed for multi-asset financial analysis rather than a sequence of manually executed scripts.

### Parallel Workflow Architecture

```text
                    AWS STEP FUNCTIONS
                      PARALLEL STATE
                            |
              +-------------+-------------+
              |                           |
       BITCOIN PIPELINE             MONERO PIPELINE
              |                           |
       BTC Market Data              XMR Market Data
       BTC Google Trends            XMR Google Trends
              |                           |
         AWS Glue ETL                AWS Glue ETL
              |                           |
       Weekly Aggregation          Weekly Aggregation
       Data Harmonization          Data Harmonization
              |                           |
       Price + Sentiment           Price + Sentiment
          Integration                 Integration
              |                           |
       BTC Final Dataset            XMR Final Dataset
              |                           |
              +-------------+-------------+
                            |
                 COMPLETED WORKFLOWS
                            |
                   AMAZON REDSHIFT
                            |
                   AMAZON QUICKSIGHT
                            |
               COMPARATIVE FINANCIAL
                    INTERPRETATION
```

The two branches follow equivalent analytical objectives but retain independent transformations and execution paths.

AWS Step Functions coordinates their execution through a Parallel state, enabling simultaneous processing of the asset-specific workflows.

### Why Parallel Execution Is Important

The architecture demonstrates several capabilities relevant to financial data platforms.

**Concurrent Processing**

Bitcoin and Monero transformations can execute simultaneously rather than requiring strictly sequential processing.

**Independent Asset Logic**

Each cryptocurrency can accommodate differences in source data structure and cleaning requirements without compromising the common analytical framework.

**Centralized Orchestration**

AWS Step Functions coordinates the execution of multiple Glue jobs through explicit state transitions and completion conditions.

**Scalability**

The architecture can be extended to additional cryptocurrencies or financial instruments by introducing new processing branches.

**Analytical Standardization**

Independent pipelines generate comparable datasets, supporting consistent downstream analysis.

The project demonstrates the implementation of parallel orchestration, although the report does not quantify execution-time improvements against a sequential benchmark.

The principal achievement is therefore the **architectural capability to coordinate and execute multiple financial data workflows concurrently**.

## 4. End-to-End AWS Cloud Architecture

The project integrates AWS services into a structured financial data processing environment.

The architecture separates raw data storage, transformation, workflow orchestration, analytical storage and visualization.

| AWS Service | Function |
|---|---|
| Amazon S3 | Raw, processed and final analytical data storage |
| AWS Glue ETL | Financial data cleaning, transformation, aggregation and integration |
| Apache Spark / PySpark | Distributed data processing within Glue |
| AWS Step Functions | Workflow orchestration and parallel execution |
| Amazon Redshift | Analytical data warehousing and SQL queries |
| Amazon QuickSight | Financial data visualization and market interpretation |

The services operate as components of a coordinated end-to-end architecture.

### Amazon S3: Three-Layer Data Architecture

The project uses three S3 storage environments corresponding to different stages of the data lifecycle.

**Raw Layer – `bucketraw`**

Contains the original Bitcoin and Monero historical price datasets and their corresponding Google Trends files.

**Processed Layer – `bucketargent`**

Contains cleaned and transformed datasets, including weekly average cryptocurrency prices aligned with the observation frequency of Google Trends.

**Final Analytical Layer – `bucketgolden`**

Contains the integrated datasets combining cryptocurrency prices with the corresponding search-interest indicators.

The transformed and final datasets are stored in Apache Parquet format.

This architecture provides a structured separation between original source information, intermediate transformations and analytical outputs.

It also supports future reuse of the data processing methodology.

## 5. Financial Data Integration with AWS Glue and PySpark

### Data Sources

The project uses four original CSV datasets:

| Dataset | Description |
|---|---|
| BTC_History_Data | Bitcoin historical prices |
| BTC_Google_Trends | Bitcoin-related Google search interest |
| XMR_History_Data | Monero historical prices |
| XMR_Google_Trends | Monero-related Google search interest |

The financial datasets contain daily market observations, including closing prices, opening prices, daily highs and lows, trading volumes and percentage changes.

The Google Trends datasets provide weekly search-interest observations.

Google Trends measures relative search interest through a normalized index ranging from 0 to 100.

This index represents search popularity within the selected query and historical period, rather than an absolute number of searches or a direct measure of investor transactions.

### Harmonizing Financial Prices and Online Interest

A central analytical challenge is the difference between the measurement frequencies of the two data sources.

Cryptocurrency prices are observed daily, whereas the Google Trends datasets use weekly observations.

AWS Glue ETL transformations resolve this inconsistency by calculating weekly average prices corresponding to the Google Trends observation periods.

This process ensures that both variables refer to comparable historical intervals.

The project also applies asset-specific data cleaning procedures to address differences in the original price files.

For Bitcoin, the transformations handle invalid or incorrectly formatted price observations.

For Monero, the price column requires additional adjustments to accommodate its original data representation.

The resulting transformations are implemented using AWS Glue and PySpark.

### Final Integrated Datasets

For each cryptocurrency, the transformed price series is joined with its corresponding Google Trends observations.

The final analytical structure is standardized:

| Variable | Description |
|---|---|
| Date | Weekly observation date |
| Price | Weekly average cryptocurrency price |
| GoogleTrendIndex | Normalized search-interest index |

Two independent datasets are produced:

**Bitcoin:** weekly BTC prices integrated with Bitcoin-related Google search interest.

**Monero:** weekly XMR prices integrated with Monero-related Google search interest.

Both datasets are saved in Parquet format in the final S3 storage layer.

The common structure is essential for comparative financial analysis because it allows the same analytical methodology to be applied to both assets.

## 6. AWS Step Functions: Orchestrating Two Financial Pipelines

The project uses AWS Step Functions to automate the execution of the Glue ETL transformations.

Separate state machines coordinate the processing of Bitcoin and Monero data.

Within each workflow, the initial data preparation stage is followed by the integration of historical prices and Google Trends observations.

The workflows include execution states, transitions, completion conditions and error handling.

### Bitcoin Workflow

The Bitcoin pipeline processes the historical BTC market data and corresponding Google Trends observations.

The first Glue transformation prepares and aligns the datasets.

The second transformation integrates the weekly average price series with the search-interest index.

The final output is stored in the analytical S3 layer.

### Monero Workflow

The Monero pipeline follows the same overall structure, with transformations adapted to the characteristics of the XMR source data.

The final output uses the same analytical variables as the Bitcoin dataset.

### Parallel State Implementation

The two workflows are then incorporated into an AWS Step Functions Parallel state.

This enables both asset-specific branches to execute concurrently.

The parallel architecture is documented through the state-machine configurations and execution diagrams in the project report.

The implementation demonstrates how multiple independent financial data workflows can be managed through a single orchestration framework.

This is the project's most significant cloud engineering contribution.

**The system does not merely analyze two cryptocurrencies: it coordinates their independent data processing pipelines in parallel and delivers standardized outputs for comparative financial interpretation.**

## 7. Amazon Redshift: Analytical Data Warehouse

Following the transformation and integration stages, the final Bitcoin and Monero datasets are made available in Amazon Redshift.

Redshift provides an analytical environment for storing and querying the processed financial information.

The project documents the creation and querying of the corresponding analytical tables.

This layer separates the preparation of financial datasets from their subsequent analytical use.

It enables the transformed information to be accessed through SQL and supports integration with visualization tools.

The resulting architecture is suitable for extending the analysis to additional market indicators or financial instruments.

## 8. Amazon QuickSight: Comparative Financial Insights

The final stage uses Amazon QuickSight to visualize the relationship between cryptocurrency prices and Google search interest.

The project examines the historical evolution of these variables separately for Bitcoin and Monero, using a consistent analytical approach.

### Bitcoin: Changes in the Relationship Between Online Attention and Prices

The Bitcoin visualization reveals a pronounced association between Google search interest and price movements during several historical periods.

A significant change emerges around September 2020, when both series exhibit a substantial increase.

The report identifies a shift toward higher average values following this period.

This suggests that increased online attention accompanied a major change in Bitcoin's market behavior.

The relationship becomes less uniform from mid-2022.

During this later period, Bitcoin prices appear to evolve more independently from Google search interest, with the search indicator sometimes following market movements rather than preceding them.

This observation suggests that the relationship between online attention and asset prices may vary across different market conditions.

It also highlights the potential influence of additional economic, financial and contextual factors.

### Monero: A Second Independent Sentiment–Price Relationship

The Monero analysis provides an additional perspective on the relationship between online search interest and cryptocurrency prices.

The report describes a comparatively clear and consistent visual association between Monero's historical prices and its corresponding Google Trends indicator.

This finding is important because it extends the investigation beyond Bitcoin.

The presence of a visible relationship in a second cryptocurrency suggests that the association between online attention and market performance is not necessarily confined to a single asset.

However, the consistency and strength of the relationship require formal statistical validation before broader conclusions can be established.

### Comparative Interpretation: Bitcoin Versus Monero

The dual-asset design provides a more informative analytical perspective than either individual study.

Bitcoin exhibits a relationship that appears to change across historical market regimes.

Monero shows a visually more consistent association across the observed period.

These differences raise relevant questions about how online attention interacts with asset-specific market characteristics.

They also suggest that the usefulness of search-interest indicators may depend on the financial instrument and the prevailing market environment.

The project therefore supports a comparative investigation of **how two different cryptocurrencies respond to their respective patterns of online attention**.

The results are based on visual analysis. The report does not provide Pearson correlation coefficients, statistical significance tests, formal lead-lag analysis or causal inference.

Accordingly, the findings identify meaningful historical associations but do not establish that search activity causes or reliably predicts future price movements.

## 9. Financial Intelligence and Business Applications

The project establishes a cloud-based methodology for investigating the relationship between external market-attention indicators and financial asset performance. Its principal analytical value comes from applying the same research framework to two different cryptocurrencies, allowing asset-specific patterns to be interpreted within a broader comparative context.

By combining Bitcoin and Monero historical prices with their respective Google Trends indicators, the analysis provides a structured perspective on how online interest accompanies market movements and how these relationships may evolve differently across assets and historical periods.

This approach is relevant to **multi-asset investment research, market intelligence and sentiment-driven financial analysis**, particularly where external behavioral indicators are considered alongside traditional market information.

From a technological perspective, the architecture demonstrates how AWS can support the development of automated financial data platforms. The combination of **AWS Glue ETL and PySpark** enables heterogeneous market datasets to be standardized, while **AWS Step Functions** coordinates independent analytical workflows through parallel execution. **Amazon Redshift** provides a structured environment for subsequent analytical queries, and **Amazon QuickSight** supports the interpretation and communication of financial relationships.

The resulting framework can be extended to additional cryptocurrencies, financial instruments and external indicators, supporting the development of broader multi-asset analytical environments without requiring each asset to be processed through an entirely separate technological architecture.

The project's value therefore lies in connecting **comparative financial intelligence, automated data engineering and parallel cloud orchestration** within a reusable analytical methodology.

## 10. Key Results and Project Contributions

The project delivers two complementary achievements: a comparative investigation of online search interest and cryptocurrency prices, and the implementation of an AWS cloud architecture capable of coordinating both analyses in parallel.

**Financial Analysis and Comparative Insights**

The integration of two cryptocurrency price series with two independent Google Trends indicators enables the relationship between online attention and market performance to be examined across different financial assets.

The Bitcoin analysis identifies periods of pronounced association between search interest and price movements, particularly around the market shift beginning in September 2020, followed by a less consistent relationship from mid-2022.

The Monero analysis provides a second perspective, with a comparatively more consistent visual association between online search interest and market prices over the observed period.

Together, these findings demonstrate the analytical value of examining the same sentiment–price relationship across multiple assets rather than relying on a single cryptocurrency.

**AWS Architecture and Parallel Processing**

The project implements an end-to-end cloud data processing architecture integrating:

- **Amazon S3:** structured storage across raw, processed and final analytical layers.
- **AWS Glue ETL and PySpark:** transformation, cleaning, weekly aggregation and integration of financial prices with Google Trends observations.
- **AWS Step Functions:** automated orchestration of independent Bitcoin and Monero workflows through parallel execution.
- **Amazon Redshift:** analytical storage and SQL-based access to the resulting financial datasets.
- **Amazon QuickSight:** visualization and interpretation of the relationship between online attention and cryptocurrency prices.

The most significant technological result is the implementation of **two independent financial data pipelines within a single parallel orchestration framework**, enabling coordinated multi-asset processing while preserving asset-specific transformation logic.

**Methodological Reproducibility and Scalability**

The project establishes a common analytical structure for both cryptocurrencies, combining weekly average prices with normalized Google search-interest indicators.

This standardized methodology supports comparative interpretation and provides a foundation for extending the architecture to additional financial instruments and market-attention variables.

The project demonstrates the technical feasibility of coordinated parallel processing and the analytical value of a dual-asset approach, while leaving formal statistical validation of the observed sentiment–price relationships as a potential extension.

**The central contribution is the integration of two independently developed financial sentiment analyses into one automated, parallel and scalable AWS financial intelligence architecture.**

## 11. Technologies and Methodologies

| Area | Technologies and Methods |
|---|---|
| Cloud Infrastructure | Amazon Web Services |
| Data Storage | Amazon S3, Apache Parquet |
| Data Engineering | AWS Glue ETL, Apache Spark, PySpark |
| Workflow Orchestration | AWS Step Functions, Parallel State |
| Analytical Data Warehouse | Amazon Redshift, SQL |
| Data Visualization | Amazon QuickSight |
| Financial Analysis | Bitcoin, Monero, Historical Market Prices |
| External Market Indicators | Google Trends Search Interest |
| Analytical Methods | Weekly Aggregation, Time Series Alignment, Exploratory Correlation Analysis |
| Architecture | End-to-End Data Pipelines, Parallel Processing, Multi-Asset Analytics |

## 12. Project Documentation

The complete technical report documents the AWS architecture, data preparation methodology, Glue transformations, Step Functions state machines, parallel execution workflows, Redshift integration and QuickSight financial visualizations.

### Original Project Report

[Bitcoin and Monero Price Analysis with Google Sentiment](Bitcoin%20and%20Monero%20Price%20Analysis%20with%20Google%20Sentiment.pdf)

The report contains 16 pages of technical explanations, code examples, AWS configurations, execution diagrams and analytical results.

The most relevant sections include:

- **Pages 1–5:** Project objectives, AWS architecture, source datasets and financial data preparation.
- **Pages 6–11:** AWS Glue ETL transformations, Parquet storage and integration of cryptocurrency prices with Google Trends.
- **Pages 12–14:** AWS Step Functions orchestration and parallel execution of the Bitcoin and Monero workflows.
- **Page 15:** Amazon Redshift integration and analytical querying.
- **Page 16:** Amazon QuickSight visualizations and financial interpretation.

## 13. Methodological Scope and Limitations

The project combines cloud data engineering with exploratory financial analysis.

Its strongest technical contribution is the implementation of a coordinated AWS architecture that processes Bitcoin and Monero data through independent, parallel workflows.

The financial investigation examines historical relationships between weekly average cryptocurrency prices and Google search interest during 2019–2024.

Although the original research objective refers to price volatility, the documented final visualizations primarily compare price levels with the Google Trends index rather than a separately calculated volatility measure.

The observed associations are interpreted visually. The report does not include formal correlation coefficients, statistical significance tests, causal inference or validated predictive models.

The parallel execution architecture is implemented and documented, but quantitative comparisons of processing time against sequential execution are not reported.

These boundaries define the scope of the empirical evidence while preserving the project's contributions to comparative financial intelligence and cloud architecture.

## 14. Conclusion

This project demonstrates how cloud computing can support a more comprehensive approach to financial market sentiment analysis.

Its analytical contribution is the investigation of **two distinct cryptocurrency price–sentiment relationships**, providing a comparative perspective on how online search interest relates to financial asset performance.

Its technological contribution is the development of an **end-to-end AWS architecture capable of orchestrating Bitcoin and Monero processing pipelines in parallel**, integrating multiple data sources and delivering standardized analytical outputs.

The combination of these dimensions creates a reusable framework for multi-asset financial intelligence.

Rather than treating financial analysis and cloud engineering as separate activities, the project demonstrates how a coordinated technological infrastructure can expand the scope, consistency and scalability of financial research.

**Two financial assets. Two independent sentiment indicators. Two parallel processing pipelines. One integrated AWS financial intelligence framework.**
