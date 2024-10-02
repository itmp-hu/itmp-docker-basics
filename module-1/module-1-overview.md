# 1. modul elméleti áttekintés és demo - Docker Desktop telepítése, konténerek kezelése Docker környezetben

- Mik azok a konténerek?
- Konténerizáció és virtualizáció közötti különbség
- Dockerfile, Docker image és konténer fogalma
- Mire jó a Docker Hub?
- Alap docker parancsok, konténerek életciklusa

## Mik azok a konténerek?
A konténerek olyan könnyű, izolált környezetek, amelyekben alkalmazások futtathatók a szükséges függőségeikkel együtt. Minden konténer magában hordozza az alkalmazás futtatásához szükséges összetevőket, például könyvtárakat és konfigurációkat, biztosítva az alkalmazás konzisztens működését a fejlesztői géptől a gyártási környezetig.

## Konténerizáció és virtualizáció közötti különbség
- **Konténerizáció:** A konténerek az operációs rendszer szintjén vannak elkülönítve, megosztva a gazdagép OS kernelt. Ez sokkal hatékonyabbá teszi az erőforrások felhasználását.
- **Virtualizáció:** A virtualizáció során teljes operációs rendszereket futtatunk virtuális gépeken. Minden virtuális gép saját kernellel rendelkezik, ami jelentősen növeli az erőforrásigényt.

## Dockerfile, Docker image és konténer fogalma
- **Dockerfile:** Olyan szöveges fájl, amely a konténer létrehozásának lépéseit írja le. Tartalmazza az alkalmazás futtatásához szükséges utasításokat (például melyik alap image-et használjuk, milyen parancsokat futtassunk, mely fájlokat másoljuk).
- **Docker image:** A Dockerfile alapján épülő, csak olvasható sablon, amely a konténer létrehozásához szükséges összes adatot tartalmazza.
- **Konténer:** A Docker image futtatható példánya. A konténer lehetővé teszi az alkalmazás futtatását az elkülönített környezetben.

## Mire jó a Docker Hub?
A Docker Hub egy felhőalapú tároló, ahol a felhasználók megoszthatják és letölthetik a Docker image-eket. Lehetővé teszi az image-ek központi kezelését, így az alkalmazások könnyen elérhetők és megoszthatók a fejlesztők között.

## Alap docker parancsok, konténerek életciklusa
- **`docker pull`**: Egy Docker image letöltése a Docker Hubról.
- **`docker run`**: Egy konténer indítása egy megadott Docker image alapján.
- **`docker ps`**: A jelenleg futó konténerek listázása.
- **`docker stop`**: Egy futó konténer leállítása.
- **`docker rm`**: Egy konténer eltávolítása a rendszerből.
- **Konténerek életciklusa:** Egy konténer indítása a `docker run` paranccsal kezdődik, ezután futtathatunk alkalmazásokat benne. A konténert leállíthatjuk, majd eltávolíthatjuk, ha már nincs rá szükség.
