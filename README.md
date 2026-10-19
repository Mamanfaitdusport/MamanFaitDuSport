# Carnet de suivi Sport

Application monofichier (HTML + CSS + JavaScript, sans dépendance, hors ligne), packagée en APK Android avec Capacitor.

## Structure

| Chemin | Rôle |
|---|---|
| `www/index.html` | L'application (copie exacte de `carnet-sport.html`) |
| `capacitor.config.json` | `appId` `fr.kaizen.carnetsport`, `appName` « Carnet Sport » |
| `android/` | Projet Android généré par `npx cap add android` (permission `VIBRATE` ajoutée) |
| `.github/workflows/android-apk.yml` | Build de l'APK debug et publication dans une Release GitHub |

## Récupérer l'APK

Chaque push sur `main` (ou sur une branche `claude/**`), ou un lancement manuel du workflow « Android APK », produit une Release **Carnet Sport build N** avec le fichier `.apk` attaché. Sur le téléphone : ouvrir la page **Releases** du dépôt, télécharger l'APK, autoriser l'installation depuis des sources inconnues.

## Modifier l'application

Modifier `www/index.html`, puis pousser : la CI fait `npx cap sync android` et `./gradlew assembleDebug`.

En local (avec le SDK Android installé) :

```sh
npm ci
npm run build:apk
```

## Données

Stockées dans le `localStorage` de la WebView (clés `carnet-sport-library-v3`, `carnet-sport-entries`, `carnet-sport-clock-series-v1`, `carnet-sport-semaine-tasks-v4`). Elles persistent après fermeture de l'app, mais sont propres à l'APK : les données de la version navigateur ne sont pas reprises automatiquement.
