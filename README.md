# docker_training

Uruchomienie pierwszego kontenera :)
```
docker run docker/whalesay cowsay boo
```

### Podstawowe komendy:

Sciagniecie obrazu
```
docker pull IMAGE
```

Wylistowanie obrazów
```
docker images list
```

Uruchomienie obrazu
```
docker run -it IMAGE komenda
```

Wylistowanie kontenerow
```
docker ps
```

Podlaczenie sie do dzialajacego kontenera
```
docker exec -it CONTAINER bash
```

Kopiowanie danych
```
docker cp CONTAINER:SRC_PATH DEST_PATH
```

Przekierowanie portow
```
docker run -it -p 80:80 IMAGE
```

Budowanie obrazu
```
docker build -t NAZWA:tag .
```

<details><summary>Podgląd komunikacji z kontenerem</summary>
<p>

```bash
socat -d -d -t100 \
   -lf /dev/stdout \
   -v UNIX-LISTEN:/var/run/docker.debug,mode=777,reuseaddr,fork \
      UNIX-CONNECT:/var/run/docker.sock
```

```bash
DOCKER_HOST=unix:///var/run/docker.debug docker ps
```

</p>
</details>

<details><summary>Wysłanie rządania do docker engine</summary>
<p>

```bash
curl -sSf --unix-socket /var/run/docker.sock 0/containers/json
```

</p>
</details>

<details><summary>Wejście do maszyny wirtualnej linuxa</summary>
<p>

```bash
# Windows and Mac
docker run -it --rm --privileged --pid=host justincormack/nsenter1

# Mac
screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
```

</p>
</details>
