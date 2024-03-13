# Minio standalone with initial content

## Run server
To start run command in main folder:

    docker-compose up -d


## MinIO Initialization and Data Upload

This documentation details the script commands used to initialize buckets in a MinIO server and upload specific CSV files to these buckets. The script utilizes the MinIO Client (`mc`) to interact with a MinIO server, configure access, create buckets, and upload data.

## Script Operations

The script performs the following operations sequentially:

1. **Configure MinIO Host**:
    - Command:
    ```shell
    /usr/bin/mc config host add minio http://minio:9000 ${MINIO_ROOT_USER} ${MINIO_ROOT_PASSWORD};
    ```
    - This command adds a MinIO host with the alias `minio` at the URL `http://minio:9000`. Authentication is handled through environment variables `${MINIO_ROOT_USER}` and `${MINIO_ROOT_PASSWORD}`, which should be replaced with your MinIO server's root user and password, respectively.


2. **Create and Populate on  `customers` Bucket** example:

    - Create Bucket:
    ```shell
    /usr/bin/mc mb minio/customers;
    ```
    - Upload CSV:
    ```shell
    /usr/bin/mc cp /mnt/data/customers.csv minio/customers/customers.csv;
    ```
    - This part of the script creates a bucket named `customers` and uploads a file named `customers.csv` from the mounted data volume `/mnt/data` to the bucket.

 
## Usage

This script is designed for use in initializing a MinIO server with specific data sets organized into buckets. It is particularly useful for setups requiring pre-populated data for applications, ensuring that the necessary files are in place and accessible through MinIO's S3-compatible storage service.

Remember to replace the `${MINIO_ROOT_USER}` and `${MINIO_ROOT_PASSWORD}` variables in '.env' file with your MinIO server's root user and password to ensure the script can authenticate and execute the operations successfully.

Access the MinIO console at `http://localhost:9001` with the admin credentials to manage your storage.
