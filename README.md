Input: wc -l server.log
Output: 8 server.log

Input: $ awk '$(NF-1) ~ /^[45][0-9][0-9]$/' server.log

Output:
192.168.1.15 - - [01/Apr/2026:09:15:25] "GET /api/users" 500 312
10.0.0.5 - - [01/Apr/2026:09:15:30] "POST /login" 401 215
10.0.0.5 - - [01/Apr/2026:09:16:05] "POST /login" 401 215
192.168.1.15 - - [01/Apr/2026:09:17:00] "GET /api/users" 500 312
192.168.1.20 - - [01/Apr/2026:09:17:30] "GET /about" 404 128


Input: awk '{print $(NF-1)}' server.log | sort | uniq -c
Output:
 3 200
 2 401
 1 404
 2 500

Input: awk '$(NF-1) == 200' server.log | wc -l
Output: 3 

Input: awk '$5 == "\"POST" && $6 == "/login\"" && $(NF-1) == 401' server.log | wc -l
Output: 2

Input: $ awk '{print $1}' server.log | sort | uniq
Output:
10.0.0.5
192.168.1.10
192.168.1.15
192.168.1.20

