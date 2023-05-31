redis 설치하기

$ docker image pull redis
$ docker run -d --name redis-container -p 6379:6379 -dit --restart unless-stopped redis

// Redis cli (cli만 쓸거라 redis-server를 다운로드할 필요는 없지만, redis-tools가 버전이 너무 옛것이라? 풀로 다운롣받음)
$ sudo apt-get install redis-server
$ sudo chmod 777 /etc/redis/redis.conf
$ vi /etc/redis/redis.conf # => bind 127.0.0.1 로 되어있는 부분을 0.0.0.0으로 변경 후 저장 :wq!
$ sudo systemctl restart redis-server.service