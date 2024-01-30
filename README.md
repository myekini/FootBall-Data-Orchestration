
# Football Data Engineering

[![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen)](https://github.com/yourusername/FootballDataEngineering)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![GitHub Issues](https://img.shields.io/github/issues/yourusername/FootballDataEngineering.svg)](https://github.com/yourusername/FootballDataEngineering/issues)

## 🚀 Overview

This Python-based project crawls data from Wikipedia using Apache Airflow, cleans it, and pushes it to Azure Data Lake for processing.

## 📋 Table of Contents

- [Football Data Engineering](#football-data-engineering)
  - [🚀 Overview](#-overview)
  - [📋 Table of Contents](#-table-of-contents)
  - [✨ Features](#-features)
  - [🛠️ Requirements](#️-requirements)
  - [🔧 Setup](#-setup)
    - [🔍 Prerequisites](#-prerequisites)
    - [🚀 Installation](#-installation)
  - [👩‍💻 Usage](#-usage)
  - [📊 Data Sources](#-data-sources)
  - [🔍 Data Processing](#-data-processing)
  - [💾 Data Storage](#-data-storage)
  - [🔄 Workflow Orchestration](#-workflow-orchestration)
  - [📈 Monitoring](#-monitoring)
  - [🤝 Contributing](#-contributing)
  - [📝 License](#-license)

##️ 🏗️ Architecture

![System Architecture](assets%2Fsystem_architecture.png)

## ✨ Features

- Fetches data from Wikipedia.
- Cleans the data.
- Transforms the data.
- Pushes the data to Azure Data Lake.

## 🛠️ Requirements

- Python 3.9 (minimum)
- Docker
- PostgreSQL
- Apache Airflow 2.6 (minimum)

## 🔧 Setup

### 🔍 Prerequisites

Ensure you have the following prerequisites installed:

- Python 3.9 (minimum)
- Docker
- PostgreSQL
- Apache Airflow 2.6 (minimum)

### 🚀 Installation

1. **Clone the repository:**
    ```bash
    git clone https://github.com/airscholar/FootballDataEngineering.git
    ```

2. **Install Python dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

## 👩‍💻 Usage

1. **Start your services on Docker:**
    ```bash
    docker compose up -d
    ```

2. **Trigger the DAG on the Airflow UI.**

Sure, let's fill in the data source, data processing, and data storage sections based on the provided code:

## 📊 Data Sources

The project retrieves data from Wikipedia pages related to football stadiums. The information is extracted from tables on Wikipedia pages containing details about various stadiums, such as their capacity, location, and home teams.

## 🔍 Data Processing

The data processing involves the following steps:

1. **Fetching Wikipedia Page:**
   - The `get_wikipedia_page` function sends a request to the provided URL, retrieves the HTML content of the Wikipedia page, and returns it.

2. **Parsing Wikipedia Data:**
   - The `get_wikipedia_data` function utilizes BeautifulSoup to parse the HTML content and extracts data from the relevant table on the Wikipedia page.

3. **Cleaning and Transforming Data:**
   - The extracted data undergoes cleaning and transformation, including removing unnecessary characters, handling special cases, and formatting the data into a structured format.

4. **Geocoding Locations:**
   - The latitude and longitude of each stadium's location are obtained using the `get_lat_long` function from the Geopy library.

5. **Handling Duplicates:**
   - Duplicates are identified based on location and resolved by updating their coordinates.

6. **XCom Push:**
   - The cleaned and transformed data is pushed to Airflow's XCom system for communication between tasks.

## 💾 Data Storage

The processed data is stored in CSV format on Azure Data Lake Storage. The `write_wikipedia_data` function writes the cleaned and transformed data to a CSV file and saves it to the specified location on Azure Data Lake Storage.

Note: The storage account key provided in the code is a placeholder. Make sure to replace it with the actual key for your Azure Data Lake Storage account.

Please adjust the storage options and file paths in the code based on your specific Azure Data Lake Storage configuration.

Sure, let's fill in the orchestration and monitoring sections based on the provided DAG code:

## 🔄 Workflow Orchestration

The workflow orchestration in this project is managed using Apache Airflow. The DAG (Directed Acyclic Graph) named 'wikipedia_flow' orchestrates the entire data processing pipeline.

1. **Data Extraction Task:**
   - Task ID: `extract_data_from_wikipedia`
   - Description: This task extracts data from the Wikipedia page containing information about association football stadiums by capacity. It uses the `extract_wikipedia_data` function.

2. **Data Transformation Task:**
   - Task ID: `transform_wikipedia_data`
   - Description: The extracted data is then transformed using the `transform_wikipedia_data` function. This includes cleaning the data, geocoding locations, handling duplicates, and formatting it for further use.

3. **Data Storage Task:**
   - Task ID: `write_wikipedia_data`
   - Description: The final step involves writing the cleaned and transformed data to Azure Data Lake Storage. The `write_wikipedia_data` function is responsible for storing the data.

4. **Task Dependencies:**
   - The tasks are connected in a linear fashion, indicating that each subsequent task depends on the successful completion of the previous one. The dependency structure ensures a step-by-step execution of the data processing pipeline.

## 📈 Monitoring

Monitoring in Apache Airflow can be achieved through its UI and various logging mechanisms. Key monitoring points include:

- **Airflow UI:**
  - The Airflow UI provides a visual representation of DAG runs, task status, and execution details. Users can monitor task execution logs and view the overall workflow status.

- **Logging:**
  - The DAG and task execution logs capture detailed information about each step in the workflow. Users can check logs to identify issues, debug problems, or monitor the progress of the data processing tasks.

- **Task Status:**
  - Task status information, such as success or failure, is logged and can be monitored through the Airflow UI or by querying Airflow's metadata database.

- **DAG Runs:**
  - Users can track the status of DAG runs and identify any failed or skipped runs. The UI provides a historical view of DAG run executions.

Ensure that the Airflow instance is properly configured for logging, and users have the necessary permissions to access the Airflow UI for effective monitoring.

## 🤝 Contributing

We welcome contributions to enhance and improve the Football Data Engineering project. To contribute, follow these guidelines:

**Bug Reports:**
- If you encounter any issues or bugs, please submit detailed bug reports.
- Include information about the environment, steps to reproduce, and expected vs. actual behavior.

**Feature Requests:**
- Propose new features or improvements by opening feature request issues.
- Clearly describe the envisioned functionality and how it aligns with the project's goals.

**Code Contributions:**
- Fork the repository, create a branch, and submit pull requests for code contributions.
- Follow coding standards, provide thorough documentation, and ensure tests are included.

**Communication:**
- Engage in discussions through issues and pull requests.
- Respect the project's code of conduct and maintain a positive and collaborative environment.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
