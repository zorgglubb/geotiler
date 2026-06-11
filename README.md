# Visionneuse Plans Anciens

Outil cartographique en ligne pour visualiser, géoréférencer et assembler des plans anciens numérisés sur une carte interactive.

Développé pour les chercheurs, archivistes et passionnés d'histoire locale qui travaillent avec des documents cartographiques anciens (cadastres napoléoniens, plans terriers, cartes d'État-Major, atlas de Trudaine…) et souhaitent les superposer à des fonds de carte modernes ou les assembler entre eux.

## Pourquoi cet outil ?

Les plans anciens sont souvent numérisés planche par planche, avec des bordures blanches ou noires inutiles, dans des projections variées. Les assembler manuellement dans un SIG demande du temps et des compétences techniques. Cette application permet de le faire directement dans le navigateur, sans installation, sans serveur, sans envoyer vos données nulle part.

## Ce que vous pouvez faire

- **Superposer** vos scans sur OSM, Cassini IGN, État-Major IGN ou n'importe quelle source XYZ
- **Charger** une image géoréférencée (JPG, PNG, TIF/GeoTIFF) avec son worldfile en glisser-déposer
- **Découper** automatiquement l'image en tuiles XYZ 256×256 px avec transparence sur les bordures
- **Assembler** plusieurs planches adjacentes : les zones de jonction sont fusionnées pixel par pixel, les bordures blanches/noires disparaissent
- **Composer** vos tuiles avec des couches distantes (ex: plan Verniquet de Paris) pour obtenir une tuile unique combinant les deux sources
- **Exporter** l'ensemble en un ZIP de tuiles prêt à déposer sur un serveur, ou en image JPG + worldfile dans la projection de votre choix
- **Tout se passe dans le navigateur** — aucune donnée n'est envoyée, aucun compte requis, fonctionne hors ligne une fois la page chargée

## Utilisation

### Afficher une couche XYZ existante
Cliquez sur **Cassini IGN**, **État-Major IGN**, **OSM**, ou collez une URL XYZ personnalisée.

### Géoréférencer et tuiler une image
1. Cliquez sur **⊕ Géoréférencer une image**
2. Déposez votre image (JPG/PNG/TIF) et son worldfile
3. Choisissez la projection source
4. Donnez un nom de dossier (ex: `saint_maurice`, `trudaine_berry`)
5. Configurez les niveaux de zoom et la transparence des bordures
6. Cliquez **⊕ Générer** (sans ZIP) ou **⊕ Générer + télécharger ZIP**

### Fusionner plusieurs plans
- Chargez et générez les plans un par un avec le **même nom de dossier**
- Les zones de jonction sont fusionnées automatiquement dans le registre
- Cochez les couches à fusionner dans la section **"Fusionner avec les couches affichées"**
- Le ZIP final contient **toutes** les tuiles de tous les plans

### Servir les tuiles localement
```bash
# Dans le dossier dézippé :
python -m http.server 8080
# Puis dans la page, ajoutez l'URL : http://localhost:8080/nom_dossier/{z}/{x}/{y}.png
```

## Formats worldfile supportés

| Extension | Format |
|-----------|--------|
| .jgw / .JGW | JPEG World File |
| .tfw / .TFW | TIFF World File |
| .tfwx / .TFWX | TIFF World File Extended |
| .jgwx / .JGWX | JPEG World File Extended |
| .jpw / .JPW | JPEG World File |
| .pgw / .PGW | PNG World File |
| .wld / .WLD | Generic World File |

## Dépendances (CDN, aucune installation)

- [Leaflet 1.9.4](https://leafletjs.com/)
- [Proj4js 2.9.0](https://proj4js.org/)
- [GeoTIFF.js 2.1.3](https://geotiffjs.github.io/)
- [JSZip 3.10.1](https://stuk.github.io/jszip/)

## Licence

MIT
