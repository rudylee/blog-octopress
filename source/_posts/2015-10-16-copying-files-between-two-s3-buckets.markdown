---
layout: post
title: "Copying Files Between Two S3 Buckets"
date: 2015-10-16 12:00
comments: true
categories:
- AWS
---

Today, I have to copy files from one S3 bucket to another S3 bucket which sitting in separate AWS account.

Initially, I was thinking to use S3 clients ( Tranmit or Cyberduck ) to download the files first and manually upload the files again to the other S3 Bucket. However, this approach will consume a lot of bandwidth and really slow if you have a lot of files in your S3 bucket.

## s3cmd or s4cmd

After a bit of research, I found that you can easily copy files between two S3 buckets. First thing you have to do is install s3cmd or s4cmd through pip.

```bash
pip install s4cmd
```

After you finished setting up the AWS credentials, you can start the copying process.

```bash
# format
s4cmd cp s3://<source-bucket> s3://<target-bucket>/ --recursive

#example
s4cmd cp s3://rudylee-images s3://rudylee-new-images/ --recursive
```

Since my target bucket is sitting in separate AWS account, I have to set another permission to allow everyone to upload and delete files into my target bucket.

If you want to follow this approach, make sure to delete that permission after you finished with the copying.
