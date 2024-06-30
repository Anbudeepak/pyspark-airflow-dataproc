In this repository, I am Orchestrating a PySpark workflow using Apache-Airflow into Google Cloud's Dataproc cluster.

Key Points:

# Add GCP connection into Airflow
    - 1. Generate a Service account Json file from GCP > Service Accounts > Select SA > Keys 
    - 2. Place the json file into airflow/secrets/file_name.json
    - 3. mount the json file into airflow's volume:
        - under x-airflow-common::
        - under environment:
        - add "AIRFLOW__CONN_GOOGLE_CLOUD_DEFAULT: 'google-cloud-platform://?key_path=/opt/airflow/secrets/gcp-key.json'"
        - under volumes:
        - add "- ./secrets/gcp-key.json:/opt/airflow/secrets/gcp-key.json  # Mount the JSON key file"
    - 4. Goto Airflow console (web) and goto Admin > connections
    - 5. Create new (+) > Give connection name, choose connection type as Google Cloud and Enter KeyFile Path as "/opt/airflow/secrets/gcp-key.json"
    - 6. Submit.
