# This project will use S3CDN on every release

This project uses `s3cdn` github action to upload released versions to their respective AWS S3 directories.

### `release-to-s3.yml` workflow

```
name: Update AWS S3 with current release
on:
  push:
    tags:
      - "*"
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: samifiaz/gh-action-docker@master
        env:
          AWS_S3_BUCKET: ${{ secrets.AWS_S3_BUCKET }}
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_REGION: "us-west-1" # optional: defaults to us-east-1
          SOURCE_DIR: "dist" # optional: defaults to `dist` directory
```
