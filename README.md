# ctf_xinetd

> A docker repository for deploying CTF challenges

## Configuration

Put files to floder `./ctf/bin`. They'll be copied to /home/ctf. **Update the flag** at the same time.

~~Edit `./ctf/ctf.xinetd`. replace `./helloworld` to your command.~~

now put the files to floder `./ctf/bin` and rename to `./ctf/bin/pwn_file` .


You can also edit `Dockerfile, ctf.xinetd, start.sh` to custom your environment.

## dockerfile 
### Build

```bash
cd ctf
docker build -t "ctf" .
```

DO NOT use *bin* as challenge's name

### Run

```bash
docker run -d -p "0.0.0.0:pub_port:9999" -h "ctf" --name="ctf" ctf
```

`pub_port` is the port you want to expose to the public network.

## docker compose 

edit `docker-compose.yml`, replace `port: 5000:9999` to `port:  pub_port:9999`.

```bash 
docker-compose up -d 
```

`pub_port` is the port you want to expose to the public network.

## Capture traffic

If you want to capture challenge traffic, just run `tcpdump` on the host. Here is an example.

```bash
tcpdump -w helloworld.pcap -i eth0 port pub_port
```
