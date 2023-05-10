damir@AZURDRIVE-767:~$ wrk -d 60 -t 1 -c 1 --latency -s /mnt/c/mnt/get.lua http://localhost:8081/
Running 1m test @ http://localhost:8081/
  1 threads and 1 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   222.30ms  425.66ms   1.95s    85.71%
    Req/Sec    22.84     24.00    70.00     72.41%
  Latency Distribution
     50%   16.67ms
     75%  198.45ms
     90%  797.55ms
     99%    1.87s
  189 requests in 1.00m, 54.45KB read
  Socket errors: connect 0, read 1, write 0, timeout 3
Requests/sec:      3.15
Transfer/sec:      0.91KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 10 -c 10 --latency -s /mnt/c/mnt/get.lua http://localhost:8081/
Running 1m test @ http://localhost:8081/
  10 threads and 10 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   504.07ms  515.93ms   1.40s    72.97%
    Req/Sec     1.95      2.73     9.00     92.42%
  Latency Distribution
     50%  226.60ms
     75%    1.22s
     90%    1.37s
     99%    1.40s
  66 requests in 1.00m, 19.10KB read
  Socket errors: connect 0, read 4, write 0, timeout 29
Requests/sec:      1.10
Transfer/sec:     325.26B

damir@AZURDRIVE-767:~$ wrk -d 60 -t 60 -c 60 --latency -s /mnt/c/mnt/get.lua http://localhost:8081/
Running 1m test @ http://localhost:8081/
  60 threads and 60 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   679.99ms  118.43ms 750.50ms   71.43%
    Req/Sec     0.00      0.00     0.00    100.00%
  Latency Distribution
     50%  748.50ms
     75%  750.17ms
     90%  750.50ms
     99%  750.50ms
  7 requests in 1.00m, 2.06KB read
  Socket errors: connect 0, read 7752, write 203986, timeout 0
Requests/sec:      0.12
Transfer/sec:      35.05B

damir@AZURDRIVE-767:~$ wrk -d 60 -t 1 -c 1 --latency -s /mnt/c/mnt/get.lua http://localhost:8082/
Running 1m test @ http://localhost:8082/
  1 threads and 1 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    92.99ms  241.43ms   1.38s    89.57%
    Req/Sec    63.46     58.90   178.00     53.85%
  Latency Distribution
     50%    7.11ms
     75%   10.61ms
     90%  380.74ms
     99%    1.20s
  423 requests in 1.00m, 125.17KB read
  Socket errors: connect 0, read 0, write 0, timeout 6
Requests/sec:      7.04
Transfer/sec:      2.08KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 10 -c 10 --latency -s /mnt/c/mnt/get.lua http://localhost:8082/
Running 1m test @ http://localhost:8082/
  10 threads and 10 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    86.12ms  177.83ms   1.41s    91.65%
    Req/Sec    28.62      8.48    50.00     59.37%
  Latency Distribution
     50%   33.62ms
     75%   39.41ms
     90%  192.73ms
     99%    1.03s
  13422 requests in 1.00m, 3.85MB read
  Socket errors: connect 0, read 0, write 0, timeout 20
Requests/sec:    223.48
Transfer/sec:     65.67KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 60 -c 60 --latency -s /mnt/c/mnt/get.lua http://localhost:8082/
Running 1m test @ http://localhost:8082/
  60 threads and 60 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   517.56ms  317.78ms 827.32ms   85.71%
    Req/Sec     3.29      3.40    10.00     85.71%
  Latency Distribution
     50%  539.70ms
     75%  826.55ms
     90%  827.32ms
     99%  827.32ms
  7 requests in 1.00m, 2.04KB read
Requests/sec:      0.12
Transfer/sec:      34.81B