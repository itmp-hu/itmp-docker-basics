# Docker alapok
## ITMP Klub képzés infotanároknak

**2024. június 8., szombat**

Az ősz beköszöntével egy régóta várt, nagyon izgalmas képzéssel jelentkezünk. Október 12-én, szombaton, az ITMP Klub keretében egy egynapos, Docker alapok képzést szervezünk, amelyen természetesen ingyenesen vehetnek részt klubtagjaink.
Talán eddig azt gondoltad, hogy a Docker csak a kigyúrt profik eszköze, ezért soha nem is próbálkoztál vele. Itt az idő, hogy leszámoljunk ezzel a kishitűséggel, és számodra is bebizonyítsuk, hogy a konténerek a Te mindennapjaidat is megkönnyítő természetes eszközzé válhatnak. Ebben vezető mentorként Hidvégi János, a Gdanskban Európa-bajnoki aranyérmet nyert egykori webfejlesztő versenyzőnk lesz a segítségünkre, aki ma már igazi feketeöves devopsosnak számít.
A konténerezés ma már elengedhetetlen eszköze a szoftverfejlesztésnek, és a Docker ebben úttörő szerepet tölt be. Az oktatás során lehetőséged lesz megismerni a Docker alapjait, megtanulni, hogyan lehet konténereket létrehozni, és megtapasztalni, milyen módon egyszerűsítheti a szoftverfejlesztést.

Az ismertetők és élő bemutatókon túl – ahogy azt már az ITMP-kurzusokon megszokhattátok – a gyakorlatban is kipróbálhatjátok a frissen megszerzett tudást. Ebben felkészült és lelkes mentoraink lesznek a segítségetekre.

**A továbbképzés időpontja:** 2024. október 12. (szombat) 9:00-15:00

**A továbbképzés formája:** online (Microsoft Teams meeting)

**A képzés tervezett tematikája és ütemezése:**

| Időpont       | Téma                                                                      |
|---------------|---------------------------------------------------------------------------|
| **09:00 - 09:15**   | Köszöntő, technikai információk                                          |
| **09:15 - 11:00**   | 1. modul - Docker Desktop telepítése, konténerek kezelése Docker környezetben |
| 09:00 - 09:45   | 1. modul elméleti áttekintés és demó - Hidvégi János |
| 09:45 - 10:45   | 1. modul workshop -kiscsoportos, mentorált gyakorlat |
| **10:45 - 11:00**   | Kávészünet                                                                |
| **11:00 - 13:30**   | 2. modul - Alkalmazások dockerizálása, saját docker image készítése |
| 11:00 - 11:30   | 2. modul elméleti áttekintés és demó - Hidvégi János |
| 11:30 - 12:30   | 2. modul workshop -kiscsoportos, mentorált gyakorlat |
| **12:30 - 13:30**   | Ebédszünet                                                                |
| **13:30 - 14:45**   | 3. modul - A Docker Compose használata |
| 13:30 - 14:00   | 3. modul elméleti áttekintés és demó - Hidvégi János |
| 14:00 - 14:45   | 3. modul workshop -kiscsoportos, mentorált gyakorlat |
| **14:45 - 15:00**   | Kérdések és válaszok, napzárás                                            |

## Docker konténerek kezelése

### Elmélet
- Mik azok a konténerek?
- Konténerizáció és virtualizáció közötti különbség
- Dockerfile, Docker image és konténer fogalma
- Mire jó a Docker Hub?
- Alap docker parancsok, konténerek életciklusa

### Gyakorlat
- Docker Desktop telepítése
- Egy hivatalos Docker image futtatása (nginx)
- Futó konténerek listázása, részletes adatok lekérdezése
- Port-forward szabály beállítása
- A konténer logjainak vizsgálata
- A konténer megállítása, újraindítása, törlése

## Alkalmazások dockerizálása, saját docker image készítése

### Elmélet
- Mi is az a Docker image?
- Egy Docker image felépítése, rétegei
- Dockerfile szintaxis, parancsok
- Docker image építése
- Hogyan kezeljük a Docker image-ket?

### Gyakorlat
- [https://docs.docker.com/get-started/workshop/02_our_app/](https://docs.docker.com/get-started/workshop/02_our_app/)
- Dockerfile elkészítése
- Docker image buildelése a Dockerfile alapján
- Docker image elindítása (1. szekció alapján)
- Docker image publikálása a Docker Hubra (regisztráció ha szükséges, docker login, docker push)

## A Docker Compose használata

### Elmélet
- Mire jó a Docker Compose?
- Hogyan épül fel a docker-compose.yaml fájl?
- Hasznos parancsok
- Mikor érdemes Docker Compose-t használni?

### Gyakorlat
- Alkalmazás és adatbázis futtatása Docker Compose segítségével
- Alkalmazás service definiálása (image, port-forward szabályok, környezeti változók)
- Adatbázis service definiálása (MySQL image használata, port-forward szabályok, volume mount)
- PhpMyAdmin service definiálása

## Docker konténerek kezelése

### Gyakorlat: Docker Desktop telepítése és konténerek kezelése

**Cél:**
- Telepítsd a Docker Desktopot
- Indítsd el és kezeld az első konténeredet

1. **Docker Desktop telepítése**
    - Töltsd le és telepítsd a Docker Desktopot a hivatalos weboldalról.
    - A telepítés után ellenőrizd a sikeres telepítést az alábbi parancs futtatásával:
      ```
      docker --version
      ```

2. **Nginx konténer letöltése és futtatása**
    - Parancs:
      ```
      docker pull nginx
      docker run -d -p 8080:80 nginx
      ```
    - Ez a parancs letölti az Nginx képet a Docker Hubról, és elindítja azt úgy, hogy a gépeden a 8080-as portot hozzárendeli a konténer belső 80-as portjához.

3. **Futtatott konténerek listázása**
    - Parancs:
      ```
      docker ps
      ```
    - Ez a parancs kilistázza a jelenleg futó konténereket. Jegyezd meg a konténer ID-ját.

4. **Konténer naplók ellenőrzése**
    - Parancs:
      ```
      docker logs <container_id>
      ```
    - Cseréld ki a `<container_id>` részt a futó konténer ID-jára, hogy megnézd a naplókat.

5. **Konténer leállítása és eltávolítása**
    - Parancsok:
      ```
      docker stop <container_id>
      docker rm <container_id>
      ```
    - A `docker stop` parancs leállítja a futó konténert, a `docker rm` pedig eltávolítja azt a rendszerből.

## Saját Docker Image készítése

### Gyakorlat: Dockerfile létrehozása és egyedi Docker image készítése

**Cél:**
- Egy egyszerű alkalmazás dockerizálása
- Saját Docker image létrehozása és buildelése
- (Opcionális) Docker image megosztása Docker Hubon

...

**Megjegyzés:** A teljes dokumentumot itt rövidítettem a bemutató céljára. Kérlek, ezt az utolsó részt töltsd ki az eredeti tartalommal vagy igény szerint.

