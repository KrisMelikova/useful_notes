### Remote PDB with Docker

```bash
pip install remote-pdb
```
Open a remote PDB:
```python
from remote_pdb import RemotePdb
RemotePdb('172.17.0.2', 4444).set_trace()
```
Run in terminal:
```bash
rlwrap socat - tcp:172.17.0.2:4444
```
To finish debugging:
```bash
Control-c
```

>Tips:
> 1) You can find container IP with: 
> ```bash
> docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <container_name>
>```
> 2) Maybe you'll need to install rlwrap and socat:
> ```python
> RUN apt-get install rlwrap -y && apt-get install socat -y
>```
> 3) Check that port you'll use is mapped (4444:4444).
> For current case you need in Dockerfile:
> ```python
> EXPOSE 4444
> ```

[Documented here](https://python-remote-pdb.readthedocs.io/en/latest/readme.html)