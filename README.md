# Cloud Functions Training

## Content

1. [Cloud Functions Series1: Trigger Cloud Functions by Cloud Storage upload events(2nd gen)](https://medium.com/@nakamasato/cloud-functions-series1-trigger-cloud-functions-by-cloud-storage-upload-events-2nd-gen-e9f983619edc)
1. [Cloud Functions Series2: Deploy Cloud Functions from GitHub Actions](https://medium.com/@nakamasato/cloud-functions-step2-deploy-cloud-functions-from-github-actions-6b1e54b21ce)

## Local test

```
poetry run functions-framework --target hello_gcs --source src/apps/script_cloud_functions.py  --signature-type cloudevent
```

```
curl localhost:8080 \
  -X POST \
  -H "Content-Type: application/json" \
  -H "ce-id: 123451234512345" \
  -H "ce-specversion: 1.0" \
  -H "ce-time: 2020-01-02T12:34:56.789Z" \
  -H "ce-type: google.cloud.audit.log.v1.written" \
  -H "ce-source: //cloudaudit.googleapis.com/projects/PROJECT_ID/logs/data_access" \
  -d '{
        "protoPayload": {
            "resourceName": "projects/_/buckets/test-bucket/objects/object_path.txt",
            "serviceName": "storage.googleapis.com",
            "methodName": "storage.objects.create"
        }
      }'
```
