# Redis

## Setting up redis Master Replica high availability using redis Sentinels.

[You can watch the youtube step by step tutorial here](https://youtu.be/XxR6M6XQq6I)

## Docker Command Explanation

docker run --name redis-master -p 6379:6379 --network redis-net -d redis redis-server --appendonly yes

let me explain the different parts of the docker run command you provided:

docker run: This command starts a new container from an image.

--name redis-master: This option sets the name of the container to redis-master.

-p 6379:6379: This option maps port 6379 from the container to the host. This means that any traffic sent to port 6379 on the host will be forwarded to the container.

--network redis-net: This option specifies the network that the container should be connected to. In this case, it is redis-net.

-d: This option tells Docker to run the container in detached mode, which means that it will run in the background.

redis: This is the name of the image that the container is based on.

redis-server: This is the command that will be executed inside the container.

--appendonly yes: This is an argument passed to the redis-server command. It specifies that Redis should use the Append Only File (AOF) persistence method, which logs every write operation received by the server, thus improving data durability and availability in case of a crash or a power outage.


## Docker Sentinel command Explanation

Let me break down the different parts of the docker run command:

docker run: This command starts a new container from an image.

-d: This option tells Docker to run the container in detached mode, which means that it will run in the background.

--name redis-sentinel_1: This option sets the name of the container to redis-sentinel_1.

-p 26379:26379: This option maps the port 26379 from the container to the host. This means that any traffic sent to port 26379 on the host will be forwarded to the container.

--network redis-net: This option specifies the network that the container should be connected to. In this case, it is redis-net.

-v /apps/redis/sentinel/sentinel_1:/data: This option creates a volume that is mounted inside the container at the /data directory. The volume is located on the host machine at /apps/redis/sentinel/sentinel_1.

redis: This is the name of the image that the container is based on.

redis-sentinel: This is the command that will be executed inside the container.

/data/sentinel.conf: This is an argument passed to the redis-sentinel command. It specifies the location of the configuration file for the Redis Sentinel instance running inside the container.


