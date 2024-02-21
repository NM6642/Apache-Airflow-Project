# Wikipedia Data Transfer with Apache Airflow

## Overview

The Wikipedia Data Transfer project demonstrates the use of Apache Airflow for scheduling and orchestrating data transfer tasks. It involves downloading the content of the Wikipedia Main Page and saving it to a local file.

## Project Structure

### DAG (Directed Acyclic Graph)

The core of the project is the Airflow DAG named `wikipedia_data_transfer`. The DAG consists of two tasks:

- **dummy_task**: A placeholder task with no actual work, used to illustrate task dependencies.
  
- **save_http_response_task**: A PythonOperator making an HTTP request to the Wikipedia Main Page and saving the content to a local file.

### Task Dependencies

`dummy_task` is set as the upstream task for `save_http_response_task`, meaning the latter will only execute if the former completes successfully.

## Running the Project

### Set Up Airflow Environment

1. Ensure Apache Airflow is installed and configured.

2. Define Connections: Create an HTTP connection in Airflow named `http_default` with the base URL [https://en.wikipedia.org](https://en.wikipedia.org).

3. DAG Configuration: Open the DAG file `wikipedia_data_transfer.py` and configure parameters such as start date, schedule interval, and file paths.

4. Run the Scheduler: Start the Airflow scheduler to begin DAG execution.

## DAG Execution Details

The DAG is scheduled to run daily (`@daily`), starting from the specified start date. During each run, `save_http_response_task` makes an HTTP request to the Wikipedia Main Page, saving the response content to a local file (`C:/Users/Downloads/dailydata.txt`).

After a successful DAG run, check the status of each task in the Airflow web UI.
