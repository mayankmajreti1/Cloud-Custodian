# Cloud-Custodian
This folder includes cloud-custodian .yml file for - EC2 / S3 / RDS / SQS / SNS

# SET UP YOUR AWS CONFIGURATION TO YOUR EC2 INSTANCE AND SET YOUR ACCESS KEY & SECRET ACCESS KEY 
aws configure 

# STEPS TO INSTALL CLOUD-CUSTODIAN ON YOUR LINUX MACHINE (AWS) 
python3 -m venv custodian
source custodian/bin/activate
pip install c7n   

# INSTALLING CUSTODIAN MAILER IN YOUR EC2 
 pip install c7n-mailer
 
 # HOW TO SET UP 
 1 . In the AWS console, create a new standard SQS queue (quick create is fine). Copy the queue URL to queue_url in mailer.yml
 2 . In AWS, locate or create a role that has read access to the queue. Grab the role ARN and set it as role in mailer.yml
 3 . Make sure your email address is verified in SES, and set it as from_address in mailer.yml
 4 . To RUN : c7n-mailer --config mailer.yml --update-lambda && custodian run -c tag-policy.yml -s .
 
 # IF ALL THE STEPSARE DONE PROPERLY , THIS WILL SEND YOU MAIL #
