# SwissTransfer API

Une API TypeScript/Node.js pour interagir avec le service SwissTransfer : envoi, téléchargement et gestion de fichiers.

> [!IMPORTANT]  
> La fonctionnalité de **upload** ne fonctionne **plus** car Infomaniak a supprimé [leur contournement reCAPTCHA](https://github.com/xalsie/Swisstransfer/issues/1) :(
> 
> La fonctionnalité de **téléchargement** fonctionne toujours

## Fonctionnalités
- ~~Upload de fichiers vers SwissTransfer~~
- Téléchargement de fichiers
- Suivi de la progression d'upload/download
- Gestion des événements

## Installation

```bash
npm install swisstransfer-api
```

## Utilisation

### Exemple d'upload
```typescript
import { SwissTransferUploader } from './src/core/SwissTransferUploader';

const uploader = new SwissTransferUploader();
uploader.on('progress', (percent) => {
  console.log(`Progression : ${percent}%`);
});

uploader.upload('chemin/vers/fichier.zip')
  .then((result) => {
    console.log('Lien SwissTransfer :', result.link);
  })
  .catch(console.error);
```

### Exemple de téléchargement
```typescript
import { SwissTransferDownloader } from './src/core/SwissTransferDownloader';

const downloader = new SwissTransferDownloader();
downloader.on('progress', (percent) => {
  console.log(`Progression : ${percent}%`);
});

downloader.download('lienSwissTransfer', 'chemin/de/destination')
  .then(() => {
    console.log('Téléchargement terminé');
  })
  .catch(console.error);
```

## Documentation
- Voir les fichiers dans `src/core/` pour les classes principales
- Les tests sont dans `test/`

## Contribution
Les contributions sont les bienvenues !
1. Forkez le projet
2. Créez une branche
3. Proposez une Pull Request

## Licence
MIT
