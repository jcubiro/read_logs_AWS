# read_logs_AWS
Read CloudWatch logs with boto3 and a bit of Python. 

DISCLAIMER: I'm new to Python so probably my code won't be the most efficient. 


GOAL OF THE SCRIPT: Originally the script was designed for SEO purposes only, to see when and how Google Crawled a website.That's why I use the filterPattern="GoogleBot". 


The script has 3 parts. 

First, the script connects to CloudWathch logs, using boto3 https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/logs.html#client

filter_log_events(**kwargs)
Lists log events from the specified log group. You can list all the log events or filter the results using a filter pattern, a time range, and the name of the log stream.

By default, this operation returns as many log events as can fit in 1 MB (up to 10,000 log events) or all the events found within the time range that you specify. If the results include a token, then there are more log events available, and you can get additional results by specifying the token in a subsequent call. This operation can return empty results while there are more log events available through the token.

The returned log events are sorted by event timestamp, the timestamp when the event was ingested by CloudWatch Logs, and the ID of the PutLogEvents request.
Request Syntax
response = client.filter_log_events(
    logGroupName='string',
    logStreamNames=[
        'string',
    ],
    logStreamNamePrefix='string',
    startTime=123,
    endTime=123,
    filterPattern='string',
    nextToken='string',
    limit=123,
    interleaved=True|False)

Then the logs are read and a dataframe is generated with the info extracted.

Finally the dataframe can be uploaded into a Database. 

