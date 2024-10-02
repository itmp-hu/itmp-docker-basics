# 1. modul workshop - Docker Desktop telepítése, konténerek kezelése Docker környezetben

- Docker Desktop telepítése
- Egy hivatalos Docker image futtatása (nginx)
- Futó konténerek listázása, részletes adatok lekérdezése
- Port-forward szabály beállítása
- A konténer logjainak vizsgálata
- A konténer megállítása, újraindítása, törlése

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