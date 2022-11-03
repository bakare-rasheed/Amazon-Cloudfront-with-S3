## CLOUDFRONT ORIGIN GROUPS

In this project I created a cloudfront distribution(A content delivery Network) using S3 bucket and Amazon EC2 as Origins

Amazon CloudFront is a web service that speeds up distribution of your static and dynamic web content, such as .html, .css, .js, and image files, to your users. 
CloudFront delivers your content through a worldwide network of data centers called edge locations. When a user requests content that you're serving with CloudFront,
the request is routed to the edge location that provides the lowest latency (time delay), so that content is delivered with the best possible performance.

An origin is the location where content is stored, and from which CloudFront gets content to serve to viewers
When you create a distribution, you specify the origin where CloudFront sends requests for the files.

Amazon Simple Storage Service (Amazon S3) is an object storage service offering industry-leading scalability, data availability, security, and performance. 
Customers of all sizes and industries can store and protect any amount of data for virtually any use case, such as data lakes, cloud-native applications, 
and mobile apps. With cost-effective storage classes and easy-to-use management features, 
you can optimize costs, organize data, and configure fine-tuned access controls to meet specific business, organizational, and compliance requirements.

You can use several different kinds of origins with CloudFront.
-Amazon S3 bucket
-MediaStore container
-MediaPackage channel
-Application Load Balancer, or an 
-AWS Lambda function URL.

![bucket](https://user-images.githubusercontent.com/114327344/199685484-36cf26f3-3420-4857-ab32-47a716df12f4.PNG)

*Step one
CREATING S3 BUCKET
- Name : bakare-bucket
- ACLs enabled
- Uncheck 'block all public access'

![bakare-bucket](https://user-images.githubusercontent.com/114327344/199749631-6f31b519-595c-428c-a147-27afcb53466b.PNG)


*Step two
Upload a file to S3 and make the object publicly accessible by changing the bucket policy

![object-upload](https://user-images.githubusercontent.com/114327344/199750053-cf1c85fd-f687-425e-9928-db164fcd2b3e.PNG)

![bucketpolicy](https://user-images.githubusercontent.com/114327344/199749641-3a6e425a-f15a-4645-92f1-a369b76df473.PNG)

*Step three
Creating CloudFront Distribution

![cloudfront](https://user-images.githubusercontent.com/114327344/199685884-9c95c154-b6d4-4811-a707-e41e2ea7dfba.PNG)

*Step three:
Creating Custom Error Pages
We can create custom error pages for CloudFront to return when origin returns HTTP 4xx or 5xx errors. For this, 
we have to save the error pages in a location that is accessible to CloudFront.
-A folder was created in S3 named CustumError
-Created an error.html file in my local system using Notepad.
-This custom HTML page will be used for showing errors in CloudFront.

`<html><h1>This is Error Page</h1></html>`
-Upload error.html to S3 bucket
-Create a block.html file in your local using Notepad.

`<html><h1>This content is blocked in your location!!!</h1></html>`
-Made the objects publi by configuring bucket policy


![object-upload](https://user-images.githubusercontent.com/114327344/199754855-d12b64ea-2739-4255-a3e4-b8ce9e1503e4.PNG)

![error htmlimg](https://user-images.githubusercontent.com/114327344/199754696-0960483d-5715-400c-b85b-fb353490e0d1.PNG)

![object-denired](https://user-images.githubusercontent.com/114327344/199754026-6c676871-eb32-4fac-b798-69bf9d3ffd25.PNG)

![bucketpolicy](https://user-images.githubusercontent.com/114327344/199754240-4d26edac-de16-4ad2-acee-2e3797b0df75.PNG)

![apache-page](https://user-images.githubusercontent.com/114327344/199754440-232ce7c7-2e01-45e1-b797-422d88943bf9.PNG)

-Accessed the Image through CloudFront

![cloudfront](https://user-images.githubusercontent.com/114327344/199755662-80230d20-ab2c-490d-bf84-1ec6afc610bf.PNG)

![apacchecloud](https://user-images.githubusercontent.com/114327344/199755686-b718f5a3-1cdc-48a3-af9e-cc52ba2e37c2.PNG)

-Configuring Custom Error Page
-Restricting the Geographic Distribution of Your Content


![block htmlpic](https://user-images.githubusercontent.com/114327344/199756690-8f18a71a-931b-4cee-beb1-3854aebdbd9d.PNG)

![403error](https://user-images.githubusercontent.com/114327344/199756538-4eb5aa55-fd2b-4558-98c3-715728f33337.PNG)

![blocked](https://user-images.githubusercontent.com/114327344/199756793-f8282857-b94a-485d-9069-498436941bfc.PNG)

![error htmlpic](https://user-images.githubusercontent.com/114327344/199757093-03ce86c8-d1ea-44db-be1c-d2a3a3880025.PNG)

![object-denired](https://user-images.githubusercontent.com/114327344/199757167-d68e927e-fcbe-4eb3-9b9a-9ad438a34149.PNG)

