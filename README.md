# S3 to ElastiSearch

I would like to introduce the python script that gets CSV files from AWS S3 bucket, parse information, transformations data to JSON and sends them to ElasticSearch. This script can be used for local usage as well as AWS Lambda.


## Install software

First of all, install ```python3```, for example:

```bash
$ brew install python3
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

Examples:

```bash
$ python3 s3-to-elastisearch.py --lambda=False --profile-name=default
```

Or:

```bash
$ python3 s3-to-elastisearch.py --lambda=False --role-name="role_here" --role-session="session"
```

## Authors
Created and maintained by [Vitaliy Natarov](https://github.com/SebastianUA). An email: [vitaliy.natarov@yahoo.com](vitaliy.natarov@yahoo.com).

## License
Apache 2 Licensed. See [LICENSE](https://github.com/SebastianUA/terraform/blob/master/LICENSE) for full details.
