# Data Warehouse Pipeline Project

## Project Overview
This project involves creating an ER diagram, building a data pipeline to load raw data into a lakehouse, performing data quality checks, normalizing tables, and creating a refined view to aggregate sales data.

## Table of Contents
- [ER Diagram](#er-diagram)
- [Orchestration and Transformation](#orchestration-and-transformation)
  - [Pipeline](#pipeline)
  - [PySpark Notebooks on Fabric](#pyspark-notebooks-on-fabric)
- [Tools and Technologies](#tools-and-technologies)
- [How to Run](#how-to-run)
- [Acknowledgments](#acknowledgments)

## ER Diagram
An Entity-Relationship (ER) diagram was created to represent the raw table structure and relationships inferred using column names.

Tool used for schema inference:
- **draw.io**: Used for generating the ER diagram, providing a clear visualization of relationships.

![ER Diagram](https://github.com/sufaila/GsyncRepo/blob/main/Gsync_ER.drawio.png)

## Orchestration and Transformation

### Pipeline
1. **Loading Raw Data**: Data is loaded from an external location to a lakehouse.
2. **Data Quality Checks**:
   - Ensure non-null values.
   - Verify the uniqueness of primary keys.
   - Confirm data types match expectations.
   - Check for foreign key constraints between fact and dimension tables.

3. **Staging Schema**:
   - Normalization: The hierarchy table is normalized into separate tables for each level.
   - Foreign Key Relationships: The staged fact table establishes foreign key relationships with the normalized tables.

4. **Refined Table**:
   - **mview_weekly_sales**: A materialized view that totals `sales_units`, `sales_dollars`, and `discount_dollars` by `pos_site_id`, `sku_id`, `fsclwk_id`, `price_substate_id`, and `type`.

5. **Incremental Calculation**: Transformation logic incrementally calculates totals in `mview_weekly_sales` for partially loaded data.

### PySpark Notebooks on Fabric
1. Transformation logic is implemented using PySpark notebooks on Fabric.
2. PySpark provides a scalable and efficient way to process and transform large datasets.

## Tools and Technologies
- **Microsoft Fabric**: For data extraction, transformation, and loading.
- **draw.io**: For generating ER diagrams.
- **Pipelines**: For orchestration.
- **PySpark Notebooks**: For transformation logic.

## How to Run
1. **Clone the repository**:
   ```sh
   git clone https://github.com/sufaila/GsyncRepo.git
