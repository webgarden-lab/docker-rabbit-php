# docker-rabbit-php

Tento repozitar slouzi jako source code pro Automated builds na cloudu Docker Hubu.

Docker hub sam z tohoto repozitare cte a vytvari buildy, dle toho, jak je repozitar nastaveny [zde](https://hub.docker.com/r/webgarden/rabbit-php/~/settings/automated-builds/).

**TYTO CONTAINERY I TENTO KOD JE VEREJNE DOSTUPNY, KONTAJNERY PROTO *NIKDY* NESMI OBSAHOVAT:**
- SSH Klice
- Hesla
- Casti aplikace
- Predpripravene privatni repozitare (pozor na Composer cache)


## Pridavam vetev, variantu buildu
- Vytvorim novou slozku pro Dockerfile
- Ve slozce vytvorim Dockerfile
- Otestuji na lokale pomoci `docker build <nazevSlozky>/. --tag <nazev_conttaineru_pro-test>`

- Pripravim prostredi na [Docker Hubu](https://hub.docker.com/r/webgarden/rabbit-php/~/settings/automated-builds/)
- commitnu smysluplnou message
- pushnu
- Cekam na zpravy z [Logu](https://hub.docker.com/r/webgarden/rabbit-php/builds/)

- Pouzivam svuj container.

## Dalsi repozitare stejneho zamereni
- [Webgarden/buddy](https://github.com/webgarden-lab/docker-buddy) 
- [Webgarden/php](https://github.com/webgarden-lab/docker-php)
- [Webgarden/node](https://github.com/webgarden-lab/docker-node)
- [Webgarden/rabbit-php](https://github.com/webgarden-lab/docker-rabbit-php)
