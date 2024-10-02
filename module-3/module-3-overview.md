# 3. modul elméleti áttekintés és demo - A Docker Compose használata

- Mire jó a Docker Compose?
- Hogyan épül fel a docker-compose.yaml fájl?
- Hasznos parancsok
- Mikor érdemes Docker Compose-t használni?

## Mire jó a Docker Compose?
A Docker Compose egy olyan eszköz, amely lehetővé teszi több konténerből álló alkalmazások definiálását és futtatását. Egy egyszerű konfigurációs fájlban, a `docker-compose.yaml`-ban, meghatározhatod az alkalmazásod összes konténerének beállításait, hálózati kapcsolatát, volume-ait, és környezeti változóit. A Docker Compose automatikusan elindítja és összekapcsolja ezeket a konténereket, így leegyszerűsíti a komplex alkalmazások telepítését és fejlesztését.

## Hogyan épül fel a docker-compose.yaml fájl?
A `docker-compose.yaml` fájlban határozhatod meg az alkalmazásod szolgáltatásait. A fájl szintaktikája YAML formátumot követ, és a következő fő részeket tartalmazza:
- **`services`**: Az alkalmazásod konténereit definiálja. Itt adod meg az image nevét, a futtatni kívánt parancsokat, a porttovábbításokat, valamint a környezeti változókat.
- **`volumes`**: Meghatározza a perzisztens adattárolási helyeket, amelyeket a konténerek használhatnak.
- **`networks`**: Opcionálisan konfigurálhatod a konténerek közötti hálózati kapcsolatokat.

Példa egy egyszerű `docker-compose.yaml` fájlra:
```yaml
services:
  app:
    image: my-app
    ports:
      - "3000:3000"
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:8.0
    volumes:
      - ./mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos
```

## Hasznos parancsok
- **`docker-compose up`**: Elindítja az összes szolgáltatást, amelyet a `docker-compose.yaml` fájlban definiáltál. A `-d` opcióval a háttérben futtathatod a szolgáltatásokat.
- **`docker-compose down`**: Leállítja és eltávolítja az összes futó konténert és hálózatot, amelyet a `docker-compose.yaml` fájlban definiáltál.
- **`docker-compose ps`**: Listázza az összes futó konténert a Compose projektben.
- **`docker-compose logs`**: Megjeleníti a konténerek logjait.
- **`docker-compose exec <szolgáltatás_neve> <parancs>`**: Egy parancs futtatása egy adott szolgáltatás konténerében.

## Mikor érdemes Docker Compose-t használni?
A Docker Compose akkor hasznos, ha több konténerből álló alkalmazást szeretnél futtatni és kezelni, például:
- Ha alkalmazásod különböző szolgáltatásokat használ (pl. webalkalmazás, adatbázis, cache).
- Ha fejlesztői környezetben egyszerűen szeretnéd futtatni és tesztelni az alkalmazásodat.
- Ha az alkalmazás több mikro-szolgáltatásból áll, és azok együttműködését szeretnéd szimulálni egyetlen konfigurációs fájl segítségével.
