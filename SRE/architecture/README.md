### Architectural Question

Our Load Balancer logs are exported every 5 minutes to AWS S3 and we need to be able to easily query the files when needed.
Let's say we want to figure out how many different IPs have reached a certain path on our Load Balancer during a certain period of the day.

What would be the options in order to provide a cost effective solution for that requirement? 
Considering that we store 2TB of load balancer logs per month, how much would your solution cost?
Discuss the trade-offs of your solution.