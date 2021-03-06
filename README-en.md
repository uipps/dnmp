Docker deploying Nginx MySQL PHP7/PHP5.6/PHP8.0 in one key, support full feature functions.

**[[中文说明]](README.md)**

![Demo Image](./dnmp.png)

## 1. Feature
1. Completely open source.
2. Support Multiple PHP version(PHP8.0, PHP5.6, php7.4) switch.
3. Support Multiple domains.
4. Support HTTPS and HTTP/2.
5. PHP source located in host.
6. MySQL data directory in host.
7. All conf files located in host.
8. All log files located in host.
9. Built-in PHP extensions install commands.
10. Promise 100% available.
11. Supported any OS with docker.

## 2. Usage
1. Install `git`, `docker` and `docker-compose`;
2. Clone project:
    ```
    $ git clone https://github.com/uipps/dnmp.git
    ```
3. Add current user to group `docker`：
    ```
    $ sudo gpasswd -a ${USER} docker
    ```
4. Start docker containers:
    ```
    $ cd dnmp
    $ cp env.sample .env       # Use copy command on Windows
    $ docker-compose up
    ```
    You may need use `sudo` before this command in Linux.
5. Go to your browser and type `localhost`, you will see:

![Demo Image](./snapshot.png)

The index file is located at `./www/localhost/index.php`.


## 3.Multiple php version
Default, we create 3 php container, they are php7.4, PHP5.6 and PHP8.0,

We can change easy by modify Nginx configuration `fastcgi_pass`.

For example, [http://localhost](http://localhost) use PHP8.0, Nginx `fastcgi_pass` is:
```
    fastcgi_pass   php80:9000;
```
To use php7.4, change it:
```
    fastcgi_pass   php74:9000;
```
Then reload nginx:
```bash
$ docker exec -it dnmp_nginx_1 nginx -s reload
```
Done.

## 4. License
MIT
