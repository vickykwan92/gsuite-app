This is a repo for developing a GSuite app that will fetch Google Sheets, listen to change logs on these sheets, and eventual destination being the snowflake database, and Looker connection based on Snowflake.

# Workflow

1. Set up Push Notifications on Google Drive API v3: https://developers.google.com/drive/api/v3/push

2. Set up an HTTP triggered Cloud Function that listens to incoming notifications. Register the URL on Google Search Console, thus completing the first step of Step 1. (See tutorial)

3. Engineer CF from step 2 to store the payload in GS bucket. Need to update the service account that is being used by this CF to allow `storage.buckets.get` access, by calling `gsutil acl ch -u foo@developer.gserviceaccount.com:W gs://example-bucket` in the GCP Cloud Shell. If necessary, double check the bucket permission to allow this service account to be able to read/write.
