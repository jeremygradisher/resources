1. Create IAM user and grab the keys:
Click Users in the left hand navigation
 - Add Users button in upper right hand corner.

2. Within User details, create a User name and select Provide user access to the AWS Management Console - which will give us an access point to make changes or address issues. In this instance I selected "I want to create an IAM user"

3. Go ahead and create without attaching a policy. We will come back to that.

That gave me:
Console sign-in URL:

User name:

Console password:

4. Create the S3 bucket - Click create bucket. Name it. AWS Region matters - Currently deselecting the Block all public access setting.

bucketname: 

Create and Connect policy to the User!:
5. Go back to services and click IAM hit users in the left nav and click into the user

6. hit policies in the left click get started (if necessary) 

7. click create policy - Use JSON

8. Attach policy to IAM user created
Here is a sample policy, replace the code with your s3 bucket name as needed below:
```
{
"Version": "2012-10-17",
"Statement": [
{
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
            "arn:aws:s3:::bucketname",
            "arn:aws:s3:::bucketname/*"
            ]
},
{
"Effect": "Allow",
"Action": "s3:ListAllMyBuckets",
"Resource": "arn:aws:s3:::*"
}
]
}
```
9. hit Next - name the policy
Policy name: 

10. go to users and attach the policy under permissions attach policy

11. Click back into the user and create the access keys that you need - choose just the cli:
Now we have what we need:

user: 
Access Key ID: 
Secret Access Key: 
bucket: 
region: 


Once I have those keys, I will have everything I need.