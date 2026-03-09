# ArchDev Partners Website

Static website for [archdev.pro](https://archdev.pro).

## Hosting

- **S3 bucket** serves the static files
- **CloudFront** provides CDN and HTTPS
- **Cloudflare** manages DNS for the archdev.pro domain

## Deploying updates

Upload `index.html` to the S3 bucket:

```bash
aws s3 cp index.html s3://YOUR-BUCKET-NAME/index.html
```

Then invalidate the CloudFront cache so changes appear immediately:

```bash
aws cloudfront create-invalidation --distribution-id YOUR-DISTRIBUTION-ID --paths "/*"
```

## Files

- `index.html` — the entire site (single page, all styles inline)
- `README.md` — this file (excluded from publishing)
