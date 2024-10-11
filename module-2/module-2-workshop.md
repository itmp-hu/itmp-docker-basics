# 2. modul workshop - Saját Docker image készítése

- [https://docs.docker.com/get-started/workshop/02_our_app/](https://docs.docker.com/get-started/workshop/02_our_app/)
- Dockerfile elkészítése
- Docker image buildelése a Dockerfile alapján
- Docker image elindítása (1. szekció alapján)
- Docker image publikálása a Docker Hubra (regisztráció ha szükséges, docker login, docker push)

**Cél:**
- Egy egyszerű alkalmazás dockerizálása
- Saját docker image létrehozása és buildelése
- (Opcionális) Docker image megosztása Docker Hubon

**1. Alkalmazás repo klónozása**
Klónozd vagy tölts le a példaalkalmazást GitHubról: [https://github.com/docker/getting-started-app/tree/main](https://github.com/docker/getting-started-app/tree/main)

**Parancs:**
```bash
git clone https://github.com/docker/getting-started-app/tree/main example-app
```

**2. Dockerfile Létrehozása**
Navigálj az alkalmazást tartalmazó mappába, és hozz létre egy új fájlt “Dockerfile” néven a következő tartalommal:
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

**3. Docker image buildelése**
Az alkalmazás mappájában futtasd le a következő parancsot a docker image építéséhez.

**Parancs:**
```bash
docker build . -t my-app
```
Ez a parancs a Dockerfile-ban lévő utasítások alapján létrehoz egy docker image-et “my-app” néven. Ezután ezt az image-et használhatod konténerek létrehozására.

**4. Indítsd el az alkalmazást**
Miután elkészült a docker image, hozz létre belőle egy konténert.

**Parancs:**
```bash
docker run -d -p 3000:3000 my-app
```

**5. Ellenőrizd az alkalmazás működését**
Az előző gyakorlat során megismert parancsok segítségével ellenőrizd, hogy elindult-e az alkalmazás, nézd meg a logjait, és ha mindent rendben találsz, akkor próbáld meg betölteni a [http://localhost:3000](http://localhost:3000) címen.

**6. Docker image megosztása Docker Hubon (opcionális)**
- Regisztrálj a [https://hub.docker.com/](https://hub.docker.com/) oldalon.
- Lépj be a felhasználóneved és jelszavad segítségével a `docker login` paranccsal.
- Használd a `docker push my-app` parancsot az image megosztására.

**7. Nginx image készítése (opcionális)**
- Készíts egy saját image-et a `nginx:latest` base image felhasználásával
- Készíts egy `index.html` fájlt
- Másold fel a fájlt a `/usr/share/nginx/html` helyre
- Nevezd el az image-et `nginx-custom` néven
- Futtass egy konténert az új image felhasználásával
