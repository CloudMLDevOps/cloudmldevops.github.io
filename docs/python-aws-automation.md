## Python Boto3 Script
1) Start, Stop, Restart & Terminate EC2 instance

```python
import boto3
import sys

def manage_ec2_instance(instance_id, action):
    ec2 = boto3.client('ec2')
    
    actions = {
        'start': 'start_instances',
        'stop': 'stop_instances',
        'restart': 'reboot_instances',
        'terminate': 'terminate_instances'
    }
    
    if action not in actions:
        print(f"Invalid action: {action}. Use 'start', 'stop', 'restart', or 'terminate'.")
        return
    
    try:
        response = getattr(ec2, actions[action])(InstanceIds=[instance_id])
        print(f"{action.capitalize()} action initiated for instance {instance_id}.")
        print(response)
    except Exception as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    if len(sys.argv) != 3:
        print("Usage: python script.py <instance_id> <action>")
        sys.exit(1)
    
    instance_id = sys.argv[1]
    action = sys.argv[2].lower()
    manage_ec2_instance(instance_id, action)
```

- Execution Command

```bash
python script.py i-0qwert1234adad678 start
```

2) Identify and delete unused Elastic Block Store (EBS) volumes to reduce costs.

```python
import boto3

def delete_unused_ebs_volumes():
    ec2 = boto3.client('ec2')
    volumes = ec2.describe_volumes(Filters=[{'Name': 'status', 'Values': ['available']}])
    for volume in volumes['Volumes']:
        ec2.delete_volume(VolumeId=volume['VolumeId'])
        print(f"Deleted volume: {volume['VolumeId']}")

# Example usage:
delete_unused_ebs_volumes()
```

3) Cleanup Old Lambda Function Versions

```python
import boto3

def cleanup_old_lambda_versions(function_name):
    lambda_client = boto3.client('lambda')
    versions = lambda_client.list_versions_by_function(FunctionName=function_name)['Versions']

    for version in versions:
        if version['Version'] not in ['$LATEST']:
            lambda_client.delete_function(FunctionName=function_name, Qualifier=version['Version'])
            print(f"Deleted Lambda version {version['Version']}")

# Example usage:
cleanup_old_lambda_versions('my-lambda-function')
```

4) Monitor AWS Billing Costs

```python
import boto3

def get_aws_billing():
    ce = boto3.client('ce')
    response = ce.get_cost_and_usage(
        TimePeriod={'Start': '2023-01-01', 'End': '2023-01-31'},
        Granularity='MONTHLY',
        Metrics=['BlendedCost']
    )
    print(f"AWS Billing Cost: {response['ResultsByTime'][0]['Total']['BlendedCost']['Amount']} USD")

# Example usage:
get_aws_billing()
```

5) Identify and stop underutilized instances.

```python
import boto3

def stop_idle_instances():
    ec2 = boto3.client('ec2')
    instances = ec2.describe_instances(Filters=[{'Name': 'instance-state-name', 'Values': ['running']}])

    for reservation in instances['Reservations']:
        for instance in reservation['Instances']:
            if instance['CpuOptions']['CoreCount'] < 5:
                ec2.stop_instances(InstanceIds=[instance['InstanceId']])
                print(f"Stopped idle instance {instance['InstanceId']}")

# Example usage:
stop_idle_instances()
```

6) DynamoDB Data Export to S3
```python
import boto3

def export_dynamodb_to_s3(table_name, bucket_name, file_name):
    dynamodb = boto3.resource('dynamodb')
    s3 = boto3.client('s3')
    table = dynamodb.Table(table_name)
    data = table.scan()['Items']
    s3.put_object(Bucket=bucket_name, Key=file_name, Body=str(data))
    print(f"Data exported to s3://{bucket_name}/{file_name}")

# Example usage:
export_dynamodb_to_s3('my-table', 'my-bucket', 'backup.json')
```

7) Set up CloudWatch alarms to monitor AWS resources and receive notifications on specific metrics.
```python
import boto3

def create_cloudwatch_alarm(instance_id, threshold=70.0):
    cloudwatch = boto3.client('cloudwatch')
    cloudwatch.put_metric_alarm(
        AlarmName=f'CPU_Utilization_{instance_id}',
        MetricName='CPUUtilization',
        Namespace='AWS/EC2',
        Statistic='Average',
        Period=300,
        EvaluationPeriods=1,
        Threshold=threshold,
        ComparisonOperator='GreaterThanThreshold',
        AlarmActions=['<SNS_TOPIC_ARN>'],
        Dimensions=[{'Name': 'InstanceId', 'Value': instance_id}]
    )
    print(f"CloudWatch alarm created for {instance_id}")

# Example usage:
create_cloudwatch_alarm('i-1234567890abcdef0')
```

8) Identify and delete unused Elastic Block Store (EBS) volumes to reduce costs.

```python
import boto3

def delete_unused_ebs_volumes():
    ec2 = boto3.client('ec2')
    volumes = ec2.describe_volumes(Filters=[{'Name': 'status', 'Values': ['available']}])
    for volume in volumes['Volumes']:
        ec2.delete_volume(VolumeId=volume['VolumeId'])
        print(f"Deleted volume: {volume['VolumeId']}")

# Example usage:
delete_unused_ebs_volumes()
```

9) Reduce AWS Lambda storage usage by deleting old versions.

```python
import boto3

def cleanup_old_lambda_versions(function_name):
    lambda_client = boto3.client('lambda')
    versions = lambda_client.list_versions_by_function(FunctionName=function_name)['Versions']

    for version in versions:
        if version['Version'] not in ['$LATEST']:
            lambda_client.delete_function(FunctionName=function_name, Qualifier=version['Version'])
            print(f"Deleted Lambda version {version['Version']}")

# Example usage:
cleanup_old_lambda_versions('my-lambda-function')
```

10) Check for Open Security Groups:
```python
import boto3

def check_open_security_groups():
    ec2 = boto3.client('ec2')
    groups = ec2.describe_security_groups()['SecurityGroups']
    
    for group in groups:
        for permission in group['IpPermissions']:
            for ip_range in permission.get('IpRanges', []):
                if ip_range['CidrIp'] == '0.0.0.0/0':
                    print(f"Security Group {group['GroupId']} has open access!")

check_open_security_groups()
```