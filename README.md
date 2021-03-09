# image-lambda

## How to Use
To use my lambda function I simply need to upload a photo to my S3 bucket titled 401bucketthumbnail and with the trigger I set up on it, it will output a 50x50 pixel thumbnail of the same image to my 401bucketthumbnail-resize S3 bucket. The new image will have the same name as the old but with the prefix -resized.

## Issues During Set-Up
* I ran into several issues during setup, the first being that my permissions were being denied when trying to create my lambda function through the cli. I did some research and found that I could set my permissions to full access on s3 to alleviate the issue. It was stated that this is not the best solution in the real world because it involves giving users greater permissions than they need, however, for a lab it said it would work well to complete the assignment. [Source A Cloud Guru](https://acloud.guru/forums/aws-cda-2018/discussion/-M4m0vlMrJjtsdDWBklX/not%20authorized%20to%20perform%20lambda:CreateFunction%20on%20resource)
* The next issue I ran into was that my sizing of my thumbnail was wrong per the lab instructions and so I needed to change the sharp.resize parameters and then re-zip the file. Upon doing so when I tried to use the create function command it would not let me because I already had that function created. I was able to find the code to update the function ```aws lambda update-function-code`` and using that was able to correct my lambda function
* The last issue I ran into was that my functions were not visible in my lambda console even though they were performing their functions when I utilized them through the cli. I refreshed the lambda console several times to no avail before exiting out of it and reopening it at which point the functions were visible and I was able to add a trigger.

## Images

### Original
![](./assets/cat.jpg)

### Thumbnail
![](./assets/resized-cat.jpg)

## References
* [AWS Tutorial](https://docs.aws.amazon.com/lambda/latest/dg/with-s3-example.html)
* [Paul Sovik, Create a Lambda Function](https://medium.com/swlh/create-a-lambda-function-with-aws-command-line-interface-55e5f2af92e1)