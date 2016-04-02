#S3ditor

S3ditor allows you to make changes to your static files hosted on AWS S3 bucket from the comfort of your browser without requiring you to install any software on your machine.

### Steps to use S3ditor:
* Login into your AWS Console and go to S3. Edit the CORS Configuration of your Bucket 
```data
<?xml version="1.0" encoding="UTF-8"?>
<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
    <CORSRule>
        <AllowedOrigin>http://sagarmhatre.github.io</AllowedOrigin>
        <AllowedMethod>GET</AllowedMethod>
        <AllowedMethod>PUT</AllowedMethod>
        <AllowedMethod>POST</AllowedMethod>
        <MaxAgeSeconds>3000</MaxAgeSeconds>
        <AllowedHeader>*</AllowedHeader>
    </CORSRule>
</CORSConfiguration>
```
* Login into your AWS Console and go to IAM. 
* Create a policy with full access to your bucket
```data
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "s3ditor",
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws:s3:::mybucket"
            ]
        }
    ]
}
```
(You may be able to fine grain the access control. Just ensure that the policy has permissions to list all the files, get the file content & update it)
* Create a user with the above created Permission.
* Create an Access Key & Download the Credentials. Open the CSV file that gets downloaded.
* Navigate to [S3ditor](http://sagarmhatre.github.io/s3ditor/). Copy the Access Key Id & Secret Access Key from the csv downloaded in the above step to the respective fields in the Login Form. Select your region & type the name of your Bucket. Click Login


### Steps to use S3 bucket as a website :
* Login into your AWS S3 console, create a bucket and upload your webpages to the bucket
* To make your bucket available on the internet as a website, Edit your bucket policy as
```data
        {
        	"Version": "2012-10-17",
        	"Statement": [
        		{
        			"Sid": "PublicReadGetObject",
        			"Effect": "Allow",
        			"Principal": "*",
        			"Action": "s3:GetObject",
        			"Resource": "arn:aws:s3:::website-for-training/*"
        		}
        	]
        }
```
