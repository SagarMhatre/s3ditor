Welcome to S3ditor. 
            
1. Edit your CORS Configuration to allow http://sagarmhatre.github.io/

               <?xml version="1.0" encoding="UTF-8"?>
               <CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
                   <CORSRule>
                       <AllowedOrigin>http://sagarmhatre.github.io/</AllowedOrigin>
                       <AllowedMethod>GET</AllowedMethod>
                       <AllowedMethod>PUT</AllowedMethod>
                       <AllowedMethod>POST</AllowedMethod>
                       <MaxAgeSeconds>3000</MaxAgeSeconds>
                       <AllowedHeader>*</AllowedHeader>
                   </CORSRule>
               </CORSConfiguration>

2. Create a user with AmazonS3FullAccess & Create an Access Key for it. Enter them on the login page
