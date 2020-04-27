# S3 to ElastiSearch

I would like to introduce the python script that gets CSV files from AWS S3 bucket, parse information, transformations data to JSON and sends them to ElasticSearch. This script can be used for local usage as well as AWS Lambda.


## Install software

First of all, install ```python3```, for example:

```bash
$ brew install python3
```

NOTE: You have to install HOMEBREW, the command here:

```bash
$ sudo /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

Secondly, installing PIP:

```bash
$ sudo easy_install pip
```

After that, install requiriments:

```bash
$ pip3.7 install -r requirements.txt
```

To get help, run:

```bash
$ python3 s3-to-elastisearch.py --help
usage: python3 script_name.py {ARGS}

optional arguments:
  -h, --help            show this help message and exit
  --version             show program's version number and exit
  --bclient BOTO3_CLIENT
                        Set boto3 client
  --region REGION       Set AWS region for boto3
  --pname PROFILE_NAME, --profile-name PROFILE_NAME
                        Set profile name of AWS
  --rname ROLE_NAME, --role-name ROLE_NAME
                        Set role ARN name
  --rsession ROLE_SESSION, --role-session ROLE_SESSION
                        Set role session name
  --s3-bucket S3_BUCKET, --s3bucket S3_BUCKET
                        Set S3 bucket name
  --es-url ES_URL, --esurl ES_URL
                        Set ElastiSerch URL
  --lambda AWS_LAMBDA   Set lambda usage

created by Vitalii Natarov
```

## Examples:

I developed python scipt to support local usage and AWS Lambda.

### Local usage

If you want to run locally, you can use one of the next commands:

```bash
$ python3 s3-to-elastisearch.py --lambda=False --profile-name=default
```

Or:

```bash
$ python3 s3-to-elastisearch.py --lambda=False --role-name="role_here" --role-session="session"
```

### AWS Lambda

To use this python script as AWS Lambda, you must add the next environment variables inside AWS Lambda:

- aws_s3_bucket_name - Set AWS S3 bucket name where the CSV files will be located.
- elasticsearch_url -  Set the URL where the ElasticSearch located is. For Ex: "localhost:9200".
- aws_boto3_client - Set client for boto3.
- aws_region - Set the region for AWS usage.
- aws_profile_name - The name of a profile to use. It can be skipped if planned to use the AWS IAM role with session parameters (parameters below).
- aws_role_name - If aws_profile_name is not set, this parameter MUST be specified as AWS IAM role to allow AWS Lambda gets AWS resources.
- aws_role_session - If aws_profile_name is not set, this parameter MUST be specified as AWS IAM session for aws_role_name.

![Lambda_envs.png](https://github.com/SebastianUA/lambda-s3-elastisearch/blob/master/additional_files/pics/Lambda_envs.png)

The AWS IAM policies and roles located at `./additional_files/iam` folder and can be used for that script.


## Authors
Created and maintained by [Vitaliy Natarov](https://github.com/SebastianUA). An email: [vitaliy.natarov@yahoo.com](vitaliy.natarov@yahoo.com).

## License
Apache 2 Licensed. See [LICENSE](https://github.com/SebastianUA/terraform/blob/master/LICENSE) for full details.
