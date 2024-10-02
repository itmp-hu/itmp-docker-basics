# 3. modul workshop - A Docker Compose használata

- Alkalmazás és adatbázis futtatása Docker Compose segítségével
- Alkalmazás service definiálása (image, port-forward szabályok, környezeti változók)
- Adatbázis service definiálása (MySQL image használata, port-forward szabályok, volume mount)
- PhpMyAdmin service definiálása

## Gyakorlat: Több Konténeres Alkalmazás Futtatása Docker Compose Segítségével

**Cél:**
- Docker-compose.yaml leíró létrehozása
- Több konténerből álló alkalmazás kezelése Docker Compose-zal

**1. Docker-compose Leíró Létrehozása**
Navigálj az alkalmazás mappájába, és hozz létre egy fájlt “docker-compose.yaml” néven a következő tartalommal:
```yaml
services:
  app:
    image: my-app
    ports:
      - 127.0.0.1:3000:3000
```

**2. Adatbázis szolgáltatás**
Az alkalmazás működéséhez szüksége van egy adatbázisra. Hozz létre ennek is egy szolgáltatást. Image-nek használd a [MySQL image-et](https://hub.docker.com/_/mysql).

Add meg a szükséges volume mount leírókat, hogy az adatbázisban tárolt adatok perzisztensen legyenek tárolva.

Konfiguráld a felhasználónevet és jelszót környezeti változók segítségével: `MYSQL_ROOT_PASSWORD` és `MYSQL_DATABASE`.

A service definíciónak így kell kinéznie:
```yaml
mysql:
  image: mysql:8.0
  volumes:
    - ./mysql-data:/var/lib/mysql
  environment:
    MYSQL_ROOT_PASSWORD: secret
    MYSQL_DATABASE: todos
```

**3. Alkalmazás konfigurálása**
Konfiguráld az alkalmazást környezeti változók segítségével, hogy az előző lépésben létrehozott adatbázist használja: `MYSQL_HOST`, `MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_DB`.

Figyelj arra, hogy a belső hálózaton az adatbázist nem a localhost-on, hanem a service nevén éred el, jelen esetben ez `mysql` lesz.

A teljes `docker-compose.yaml` leíró ezen a ponton így néz ki:
```yaml
services:
  app:
    image: my-app
    ports:
      - 127.0.0.1:3000:3000
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

**4. Docker-compose Elindítása**
Indítsd el az alkalmazást a `docker compose up -d` parancs segítségével. Ez el fogja indítani az alkalmazás és adatbázis szolgáltatást.

**5. Alkalmazás Ellenőrzése
Ellenőrizd, hogy sikeresen elindult-e az alkalmazás. Ehhez navigálj a [http://localhost:3000](http://localhost:3000) urlre.

Továbbá ellenőrizheted a létrejött konténereket a korábban ismertetett parancsok segítségével.

**6. PhpMyAdmin Szolgáltatás Konfigurálása (Opcionális)
Konfiguráld be a PhpMyAdmin szolgáltatást a dokumentáció alapján: [https://hub.docker.com/_/phpmyadmin](https://hub.docker.com/_/phpmyadmin).

**Tipp:** Nézd végig az “Environment variables summary” szekciót az elérhető konfigurációs paraméterek listájáért, és kérd a mentorok segítségét.