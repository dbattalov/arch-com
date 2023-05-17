damir@AZURDRIVE-767:~$ wrk -d 60 -t 10 -c 10 --latency -s /mnt/c/mnt/get.lua http://localhost:8081/
Running 1m test @ http://localhost:8081/
  10 threads and 10 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    29.12ms   46.35ms 647.43ms   97.57%
    Req/Sec    43.33      8.45    70.00     85.20%
  Latency Distribution
     50%   22.17ms
     75%   25.32ms
     90%   30.11ms
     99%  278.48ms
  24262 requests in 1.00m, 3.73MB read
  Socket errors: connect 0, read 0, write 0, timeout 10
  Non-2xx or 3xx responses: 24262
Requests/sec:    403.89
Transfer/sec:     63.50KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 30 -c 30 --latency -s /mnt/c/mnt/get.lua http://localhost:8081/
Running 1m test @ http://localhost:8081/
  30 threads and 30 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   112.50ms   67.34ms 772.29ms   96.60%
    Req/Sec     9.89      3.46    30.00     78.29%
  Latency Distribution
     50%  104.52ms
     75%  123.05ms
     90%  143.76ms
     99%  474.16ms
  6403 requests in 1.00m, 0.98MB read
  Socket errors: connect 0, read 0, write 0, timeout 30
  Non-2xx or 3xx responses: 6403
Requests/sec:    106.53
Transfer/sec:     16.75KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 60 -c 60 --latency -s /mnt/c/mnt/get.lua http://localhost:8081/
Running 1m test @ http://localhost:8081/
  60 threads and 60 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   177.96ms  222.23ms   1.88s    93.32%
    Req/Sec     8.72      2.60    20.00     77.27%
  Latency Distribution
     50%  113.61ms
     75%  142.86ms
     90%  247.82ms
     99%    1.44s
  24723 requests in 1.00m, 3.80MB read
  Socket errors: connect 0, read 0, write 0, timeout 71
  Non-2xx or 3xx responses: 24723
Requests/sec:    411.33
Transfer/sec:     64.67KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 10 -c 10 --latency -s /mnt/c/mnt/get.lua http://localhost:8082/
Running 1m test @ http://localhost:8082/
  10 threads and 10 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    44.72ms   89.59ms   1.12s    97.70%
    Req/Sec    30.26      7.79    60.00     55.71%
  Latency Distribution
     50%   31.63ms
     75%   36.93ms
     90%   44.85ms
     99%  518.32ms
  10055 requests in 1.00m, 1.54MB read
  Socket errors: connect 0, read 0, write 0, timeout 10
  Non-2xx or 3xx responses: 10055
Requests/sec:    167.33
Transfer/sec:     26.31KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 30 -c 30 --latency -s /mnt/c/mnt/get.lua http://localhost:8082/
Running 1m test @ http://localhost:8082/
  30 threads and 30 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency    84.89ms   57.77ms 799.30ms   97.41%
    Req/Sec    12.92      4.74    20.00     67.77%
  Latency Distribution
     50%   75.27ms
     75%   83.23ms
     90%   95.61ms
     99%  428.58ms
  22705 requests in 1.00m, 3.49MB read
  Non-2xx or 3xx responses: 22705
Requests/sec:    377.83
Transfer/sec:     59.40KB

damir@AZURDRIVE-767:~$ wrk -d 60 -t 60 -c 60 --latency -s /mnt/c/mnt/get.lua http://localhost:8082/
Running 1m test @ http://localhost:8082/
  60 threads and 60 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   182.52ms   67.33ms 583.51ms   79.89%
    Req/Sec     6.47      2.91    10.00     45.86%
  Latency Distribution
     50%  155.30ms
     75%  208.78ms
     90%  288.33ms
     99%  393.33ms
  19828 requests in 1.00m, 3.04MB read
  Non-2xx or 3xx responses: 19828
Requests/sec:    329.92
Transfer/sec:     51.87KB