# Capacity: reconciliation-service

Platform note: [capacity](https://github.com/subhamviky/enterprise-finance-genai-assistant/blob/main/docs/engineering/operations/capacity.md). Resources on Google Cloud: a Cloud Run service (scale to zero, never public), Firestore collections, Pub/Sub topic `recon-bank-lines` with a push subscription and a dead-letter topic, one Cloud Scheduler job (`recon-scheduled`), three service accounts. The AWS reference (Lambda, DynamoDB, SQS, EventBridge) has never been applied to a real account.

What breaks first: a transaction's item limit in one match; `duplicate_of` reading every line of a tenant (G-5); Firestore's daily allowance under a load test (none run). Measured: nothing under load.
