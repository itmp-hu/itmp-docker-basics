# 2. modul elméleti áttekintés és demo - Alkalmazások dockerizálása, saját Docker image készítése

- Mi is az a Docker image?
- Egy Docker image felépítése, rétegei
- Dockerfile szintaxis, parancsok
- Docker image építése
- Hogyan kezeljük a Docker image-ket?

## Mi is az a Docker image?
A Docker image egy olyan sablon, amely a konténer létrehozásához szükséges fájlokat, konfigurációkat és beállításokat tartalmazza. Gyakorlatilag egy előre elkészített csomag, amelyből konténereket indíthatunk. Az image-ek olvashatóak és módosításuk nélkül futtathatók konténerként.

## Egy Docker image felépítése, rétegei
A Docker image több rétegből áll, ahol minden réteg egy-egy parancs végrehajtásának eredményét tárolja. Ezek a rétegek egymásra épülnek és a Docker cache-elési technikájának köszönhetően hatékonyabbá teszik az image-ek létrehozását és frissítését. A rétegek közül az alaprendszer rétegei nem változnak, így több image megoszthatja azokat, ezáltal csökkentve az erőforrások felhasználását.

## Dockerfile szintaxis, parancsok
A Dockerfile egy szöveges fájl, amely tartalmazza a Docker image létrehozásának lépéseit. Néhány gyakran használt parancs a Dockerfile-ban:
- **`FROM`**: Meghatározza az alap image-et, amelyből kiindulunk (pl. `FROM node:18-alpine`).
- **`WORKDIR`**: Az image munkakönyvtárát állítja be, ahol a további parancsok végrehajtódnak.
- **`COPY`**: Fájlok másolása a gazdagépről az image-be.
- **`RUN`**: Parancs végrehajtása az image építése során (pl. függőségek telepítése).
- **`CMD`**: Meghatározza, hogy milyen parancsot futtasson a konténer indításakor.
- **`EXPOSE`**: Megadja a konténer által használt hálózati portokat.

## Docker image építése
A Docker image építéséhez a következő parancsot használjuk:
```bash
docker build -t sajat-image-neve .
```
Ebben a parancsban a `-t` opcióval adhatunk nevet az image-nek, a `.` pedig azt jelzi, hogy a Dockerfile a jelenlegi könyvtárban található. A build során a Docker végrehajtja a Dockerfile-ban található utasításokat, és elkészíti az image rétegeit.

## Hogyan kezeljük a Docker image-ket?
Az image-ek kezelésére különböző parancsokat használhatunk:
- **`docker images`**: Listázza a helyi gépen tárolt Docker image-eket.
- **`docker rmi <image_id>`**: Törli a megadott Docker image-et a helyi gépről.
- **`docker tag <image_id> felhasznalonev/image-nev`**: Megjelöli az image-et egy megadott névvel, például a Docker Hub-ra történő feltöltéshez.
- **`docker push felhasznalonev/image-nev`**: Feltölti az image-et a Docker Hub-ra.

Az image-ek tárolhatók a helyi gépen, vagy megoszthatók másokkal a Docker Hub-on vagy más Docker registry-kben.