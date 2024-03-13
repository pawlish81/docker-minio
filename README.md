# Quick Start for Create Bucket Service

Run `docker-compose up` to start the MinIO server and the `createbuckets` container, which configures a bucket named `data-bucket` with download and upload policies. The `createbuckets` container uses the MinIO Client to manage bucket configurations automatically upon startup, ensuring `data-bucket` is ready for use. Access the MinIO console at `http://localhost:9001` with the admin credentials to manage your storage.
