# cloudfront_prewarm

cloudfront prewarm demo

Pop list can get from link:https://www.feitsui.com/zh-hans/article/3

serverless architecture

Can be multi concurrent, multi-threaded, each file trigger a lambda for concurrent prewarm

Asynchronous call

View the prewarm results through cloudwatch log


# use shell script to invoke lambda function prewarm cloudfront

# cat file.txt

/www/a.txt

/www/b.txt

/www/c.txt

# cat cf_prewarm.sh

for file in `cat file.txt`

do

echo $file

payload="{\"filename\":\"$file\",\"cloudfront_url\":\"d1zi40b7x5dwgb.cloudfront.net\"}"

aws lambda invoke --function-name cloudfront_prewarm --invocation-type Event --payload $payload o.out

done

# deployment lambda function 
cloudfront_prewarm.py

# setup lambda 
memory 500M~

timeout 15m

