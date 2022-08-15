# AWS Static Website

To create a static website using the following services: Amazon S3, Route 53 and CloudFront, the following are needed:

* A registered domain name.
* Two S3 buckets - one that contains the code/files for the website(name starts with www) and one that handles redirects(name witout www).
The "Block Public Access" option needs to be disabled, there needs to be a bucket policy that gives get permissions to allow anyone to access the website, and an index.html document needs to be set(in bucket with www at the front).
* When someone goes to the domain name, it needs to point to index.html. So, we need a hosted zone in Route 53 where two A records need to be added. The A records will point to the CloudFront distributions, which will point to the S3 buckets.
* To make the traffic secure, we can create a certificate using the Certificate Manager and we add the www domain name and the non www name as well, selecting DNS as a validation method.
* Next, create CloudFront distributions for both buckets and set the Viewer Protocol Policy to "Redirect HTTP to HTTPS", specify the SSL certifcate created in the previous step and link the distributions to the respective S3 buckets.
  
