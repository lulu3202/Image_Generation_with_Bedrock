# Animated Movie Poster Design Project
This project generates pcitures using AWS Lambda and the Stability AI Stable Diffusion model from AWS Bedrock. The generated images are stored in an S3 bucket, and a pre-signed URL is returned to access them.

## How It Works
1. **Input:** A text prompt is passed through the API.
2. **Processing:** The prompt is sent to the Stable Diffusion model via AWS Lambda, which generates an image.
3. **Storage:** The image is saved to an S3 bucket and a pre-signed URL is returned.
![image generation](https://github.com/user-attachments/assets/f1e00fc6-fe8a-4220-8560-705cb5f4bfcd)


## API Gateway Setup
See the detailed steps to set up the API Gateway in the [API_gateway_howto.md](API_gateway_howto.md) file.

## Broad Implementation Overview
1. Create an S3 bucket
2. Create a lambda function 
 * connect to AWS bedrock
 * store image as an object in S# bucket
 * generate presigned URL for image generated
 * send URL as a response to AWS API gateway
3. Create a REST API using the AWS API Gateway to allow user to pass the ‘prompt’ and view image using Pre-Signed URL
4. Test using Postman API tool 

## Examples of Generated Images

### Prompt: "A purple unicorn"
![Image of a unicorn](images/image1.png)

### Prompt: "a white unicorn"
![Image of a purple unicorn](images/image2.png)

### Prompt: "a unicorn in Dr.Seuss style"
![An image of a unicorn with rainbow background in the style of Dr Seuss](images/image3.png)

## Code
The code used in the Lambda function can be found in the [lambda_function_image_generation_usecase.py](lambda_function_image_generation_usecase.py) file.

## How to Use
1. Clone this repository.
2. Deploy the Lambda function using the code provided.
3. Set up the API Gateway and invoke the Lambda function using a tool like Postman.
4. View the generated images in your S3 bucket or through the pre-signed URLs.

## Reference Documentation Used for writing Lambda function 
* Bedrock Runtime - https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/bedrock-runtime.html
* S3 - https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/s3.html

