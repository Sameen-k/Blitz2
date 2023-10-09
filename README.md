# Blitz2

The goal is for my application to be able to host 14,000 requests at a given time. A QA engineer sent 14,000 requests to the server. After the QA engineer tested my application, they found that 7 of them could not connect. The 7 requests received this error:

*1696439476608,5,HTTP Request,Non HTTP response code: java.net.NoRouteToHostException,Non HTTP response message: Cannot assign requested address (Address not available),blitz-c4 1-13233,text,false,2381,0,9,9,http://52.90.13.143:5000/,0,0,5*

## Diagnosis:
The issue lies with processing requests. We can note that in the error for some reason those 7 requests were unable to connect to the host. Additionally, since this instance has CloudWatch installed, when the 14,000 requests came in, a spike in CPU usage was observed. With this information, we can assume this issue is related to CPU usage.

## Resolution:
The best and most efficient solution for this would be to provision more CPU for the instance. The easiest way to do this is simply to change the instance type to one with an increased resource amount. Initially, the size of the instance was a T2 Medium so we can simply change it to the larger sized instance type, a T2 Large. After this, the instance should have enough CPU to handle and process all 14,000 requests. 
 
![Screen Shot 2023-10-08 at 2 30 05 PM](https://github.com/Sameen-k/Blitz2/assets/128739962/79f0495b-a7c1-4d0f-970c-0f03eed3cf00)

Make sure that the instance you want to change is stopped, then select it, then select actions on the top right, then instance settings, then select change instance type. 
