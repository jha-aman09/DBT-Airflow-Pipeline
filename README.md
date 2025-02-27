# DBT-Airflow-Pipeline

This repository contains the code and resources for a **Data Engineering Pipeline** using **DBT and Apache Airflow**. The project involves setting up an **ELT pipeline** with Postgres, Docker, and DBT to transform and orchestrate data workflows.

---

## 📂 Project Structure

```plaintext
.
├── airflow/
│   ├── dags/
│   │   ├── elt_dag.py               # Airflow DAG for ELT pipeline
│   │   └── airflow.cfg              # Airflow configuration
│   ├── custom_postgres/
│   │   ├── macros/
│   │   │   └── film_ratings_macro.sql  # SQL macros for DBT transformations
│   │   ├── models/example/
│   │   │   ├── actors.sql
│   │   │   ├── film_actors.sql
│   │   │   ├── film_ratings.sql
│   │   │   ├── films.sql
│   │   │   ├── specific_movie.sql
│   │   │   ├── schema.yml
│   │   │   ├── sources.yml
│   │   │   └── dbt_project.yml
│   ├── elt/
│   │   ├── Dockerfile
│   │   ├── elt_script.py             # Python script to load data from source to destination
│   │   ├── start.sh                  # Shell script to initialize services
│   ├── source_db_init/
│   │   ├── init.sql                  # SQL script to initialize source database
│   │   ├── docker-compose.yaml       # Docker Compose file for setting up the database
│   │   └── README.md
└── README.md                          # Project documentation
```

---

## 🚀 Project Workflow

### 1. **Data Pipeline Setup**
- Used **Docker** and **Docker Compose** to containerize the database and orchestrate services.
- Configured **Postgres** with two databases (**source_db** and **destination_db**).
- Used **bridge networking** to enable communication between containers.

### 2. **ELT Process**
- Created **`elt_script.py`** using `subprocess` and `time` libraries to transfer data from `init.sql`.
- Defined **Airflow DAGs** (`elt_dag.py`) to automate data extraction and loading.
- Scheduled a **CRON job** for automated execution.

### 3. **DBT Transformation**
- Configured **DBT profiles** and `dbt_project.yml`.
- Created **SQL models** to transform data efficiently.
- Utilized **macros** for reusable SQL components.
- Defined **schemas and sources** (`schema.yml`, `sources.yml`) for data consistency.

### 4. **Orchestration with Airflow**
- Initialized **Airflow web server** to monitor and manage DAGs.
- Orchestrated **ELT and DBT tasks** using Airflow.
- Implemented **task dependencies** for smooth execution.

---

## ⚙️ How to Run the Project

1. Clone this repository:
   ```bash
   git clone https://github.com/jha-aman09/DBT-Airflow-Pipeline.git
   ```
2. Navigate to the project directory:
   ```bash
   cd DBT-Airflow-Pipeline
   ```
3. Start the Docker containers:
   ```bash
   docker-compose up -d
   ```

---

## 📊 Key Features

- **Containerized Environment**: Used Docker and Docker Compose.
- **Automated ELT Pipeline**: Airflow DAGs handle extraction and loading.
- **DBT for Transformations**: Modular SQL models and macros for efficiency.
- **Airflow Orchestration**: Web UI for scheduling and monitoring workflows.
- **Scalable Architecture**: Easily extendable for new data sources and transformations.

---

## 🛠️ Potential Improvements

- Integrate **CI/CD pipelines** for deployment automation.
- Implement **logging and monitoring** for error tracking.
- Optimize **DBT models** for faster transformation.
- Extend pipeline to **cloud-based storage (AWS/GCP/Azure)**.

---

## 🧑‍💻 Author  
- **LinkedIn**: [Aman Jha](https://www.linkedin.com/in/aman--jha/)  
- **GitHub**: [Aman Jha](https://github.com/jha-aman09)
