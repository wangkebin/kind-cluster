# Complete set to run in kind env
This is a complete set you need to run the code in kind - kubernetes. It contains kbds code as well as kind configurations, kafka.
It has three clusters:
1. kbds code cluster, which contains a data fetcher, restapi sync data, and a restapi client to manage.
2. kafka cluster as message broker
3. mysql for a persistant DB. 