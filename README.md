# S3 Static Website with CloudFront

This project demonstrates hosting a static website on Amazon S3 and distributing it globally using Amazon CloudFront.  
It was built as part of my 6-month cloud engineering roadmap.

## Live Demo

The website is live and served via Amazon CloudFront:

👉 https://dwaxx9olh718h.cloudfront.net

## Architecture

Browser  
→ Amazon CloudFront (CDN)  
→ Amazon S3 (Static Website Hosting)

## Services Used

- Amazon S3
  - Static website hosting enabled
  - Public-read access via bucket policy
- Amazon CloudFront
  - CDN distribution in front of S3 website endpoint
  - HTTP to HTTPS redirection
- HTML & CSS for site content

## Project Steps

1. Created a simple static website using HTML and CSS
2. Created an S3 bucket and uploaded website files
3. Enabled static website hosting on the S3 bucket
4. Configured a bucket policy to allow public read access
5. Verified website access via the S3 website endpoint
6. Created a CloudFront distribution using the S3 website endpoint as the origin
7. Set `index.html` as the default root object
8. Verified access via the CloudFront HTTPS URL

## Lessons Learned

- CloudFront’s **Quick Create UI** does not expose the **Default root object** setting during creation  
  → It must be set **after** the distribution is created under the **General** tab

- Using the **S3 bucket endpoint** instead of the **S3 website endpoint** caused access errors  
  → CloudFront must point to the `s3-website-<region>.amazonaws.com` endpoint for static sites

- Encountered **403 / site not reachable** errors while CloudFront was still deploying  
  → CloudFront distributions take time to propagate before becoming reachable

- macOS TextEdit defaults to `.txt` files  
  → Files must be saved explicitly as `.html` and `.css` with UTF-8 encoding

## Outcome

- Successfully deployed a static website on AWS
- Delivered globally over HTTPS using CloudFront
- Live URL accessible via CloudFront
- Gained hands-on experience with real AWS configuration issues and troubleshooting

## Future Improvements

- Make the S3 bucket private
- Use CloudFront Origin Access Control (OAC)
- Add a custom domain with Route 53 and ACM
- Automate deployment using Terraform or AWS CDK