## Basic commands for AWS CLI

### uploading files to S3 Bucket
#### Upload a whole folders contents
```curl
aws s3 sync ~/Documents/FOLDER_NAME s3://BUCKET_NAME/ --acl public-read
```

`--acl public-read` - this adds public readability to all files being uploaded.