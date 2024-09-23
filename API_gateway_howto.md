# Movie Poster Design - API Gateway Setup
This document provides the step-by-step process of setting up the API Gateway and integrating it with lambda for the Movie Poster Design app.

## Step 1: Create a New REST API
- Go to **API Gateway** in the AWS Management Console.
- Click on **Create API**.
- Select **REST API**, and then click **Build**.
- Set the API name as `<yourname>`.
- Choose **Edge-optimized** for the Endpoint Type (for global users).
- Click **Create API**.

## Step 2: Create a Resource
- Name your resource and create it 


## Step 3: Create a Method
- Select the newly created resource.
- Under **Create Method**, and choose **GET**
- Choose integration type as Lambda and choose your existing lambda function and create method 


## Step 4: Under GET, go to Method request
- Click Edit and under URL query string parameters, add 'prompt' parameter and make it required 
- Change Request Validator to 'Validate query string parameters and headers'(so that when REST API is invoked, it has this query string parameter called 'prompt')
- Click Save

## Step 5: Under GET, go to Integration request
- Click Edit and go to Mapping templates and add mapping templates as 'application/json' content type along with template body{"prompt" : "$input.params(‘prompt’)} - This means the prompt we get from the REST API is converted and passed as an event in AWS lambda function

## Step 6: Deploy the API to a Stage(Dev or any other)
- Click 'Deploy API' on the top right corner
- Under New stage, add a stage name called <Dev>


## Step 7: Go to Resources on the left side 
- Go to Test module on the bottom right screen
- Under Query Strings Field, provide "prompt=image of a unicorn"
- Click Test
- If all goes well, you will get a status code 200 and the presigned URL of the generated image
- Download and view it using MS paint

## Test out using POSTMAN 
- Under GET Method, you need to add the invoke URL 
- You can get the invoke URL by navigating to Stages on the left side and clicking on GET method hierarchially 
- Provide the key as prompt and under value add your unique prompt, like "unicorn with rainbows in dr.Seuss style"
- Click 'Send'
- If all goes well, you will get a status code 200 and the presigned URL of the generated image
- Download and view it using MS paint

