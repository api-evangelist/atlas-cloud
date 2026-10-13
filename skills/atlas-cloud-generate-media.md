---
name: atlas-cloud-generate-media
description: Submit an asynchronous Atlas Cloud image, video or audio generation task and retrieve its result by polling the prediction.
api: atlas-cloud:atlas-cloud-model-api
operations:
  - post_api_v1_model_modelid
  - get_api_v1_model_prediction_id
generated: 2026-10-13
method: generated
source: https://www.atlascloud.ai/docs/predictions
---
# Generate media on Atlas Cloud

1. Authenticate with `Authorization: Bearer <API key>` (https://www.atlascloud.ai/docs/api-keys).
2. Submit the task with `post_api_v1_model_modelid` (e.g. `POST /api/v1/model/generateImage` or `generateVideo`), naming the model and its parameters. Optionally pass `webhook_url` to be notified instead of polling.
3. Read the prediction id from the response and poll `get_api_v1_model_prediction_id` until the status is terminal (`completed`, `failed` or `timeout`).
4. Do not blindly retry a submission that timed out: no idempotency key is documented and a retry can create and bill a second job. Retry only 429, 500, 503 and 504.
5. Save output URLs promptly; records and media follow the retention rules at https://www.atlascloud.ai/docs/data-retention.
