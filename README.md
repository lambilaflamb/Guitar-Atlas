# Guitar Atlas V3 — Toolbox guitariste

PWA iPhone autonome en HTML/CSS/JavaScript vanilla, sans framework et sans dépendance externe.

## Nouveautés V3

- Accordage global configurable : Standard, demi-ton/ton plus bas, Drop D/C/B, DADGAD, Open D/E/G/A/C, basse 4/5/6 cordes et basse Drop D.
- Accordages personnalisés de 4 à 8 cordes, saisis de grave vers aigu.
- Les manches, arpèges, gammes, audio, tuner et voicings utilisent l’accordage actif.
- Les formes CAGED standard ne sont utilisées qu’en accordage standard ; les Drop 2 et voicings compacts sont recalculés pour l’accordage actif.
- Accords : Notes / Intervalles / Doigté sur le manche.
- Grand manche vertical plein écran pour accords, gammes et arpèges ; grave à gauche, aigu à droite.
- Forme des repères personnalisable : rond, carré, losange, triangle, étoile, hexagone.
- 46 familles d’accords, 40 gammes/modes et 23 arpèges intégrés.
- Gammes supplémentaires : altérée, lydien dominant, bebop dominante/majeure/dorienne/mineure, phrygien dominant, locrien naturel 2, lydien augmenté, modes des mineures harmonique et mélodique, etc.
- Harmonisation automatique des gammes heptatoniques en triades ou accords de 7e, accords cliquables.
- Suggestions de gammes utilisables sur l’accord courant, cliquables.
- Accordeur chromatique utilisant le microphone et La4 réglable de 430 à 450 Hz.
- Métronome 30–300 BPM : Tap Tempo, signatures, subdivisions, accent, son et volume.
- Recherche inversée accords / gammes / arpèges.
- Accords et gammes personnalisés.
- Favoris, historique, transposition, audio WebAudio et fonctionnement hors ligne conservés.

## Tester localement

Dans le dossier :

```bash
python -m http.server 8080
```

Puis ouvrir `http://localhost:8080`.

## Installer sur iPhone

1. Publier tous les fichiers sur un hébergement HTTPS (Netlify, GitHub Pages ou Cloudflare Pages).
2. Ouvrir l’URL avec Safari sur l’iPhone.
3. `Partager` → `Sur l’écran d’accueil` → `Ajouter`.
4. Ouvrir une première fois avec Internet pour remplir le cache hors ligne.

L’accordeur nécessite l’autorisation du microphone et donc une origine HTTPS en production.

## Mise à jour depuis une version précédente

La V3 utilise le cache `guitar-atlas-v3.0.0`. Remplacer tous les anciens fichiers par ceux de cette version, ouvrir une fois l’URL dans Safari, puis relancer la PWA. Si Safari conserve une ancienne interface, supprimer l’icône de l’écran d’accueil et l’ajouter à nouveau.

## Personnalisation

Les accords et gammes ajoutés depuis l’interface sont stockés dans `localStorage`. Les accordages personnalisés le sont également.

La base intégrée est au début de `app.js` dans :

- `CHORDS`
- `SCALES`
- `ARPS`
- `TUNING_PRESETS`

Après une modification de code publiée, incrémenter la constante `CACHE` dans `service-worker.js`.


## Guitar Atlas Studio V4 — extension

Cette édition conserve les cinq rubriques principales de Guitar Atlas V3 et ajoute une rubrique **Studio** avec cinq espaces :

- **Composition** : création de grilles à partir des accords déjà présents dans le dictionnaire, suppression de mesures, transposition chromatique, lecture synthétique, sauvegarde locale et export JSON individuel.
- **Jam Studio** : génération de progressions selon une tonalité et une couleur musicale (jazz/soul, blues, funk, rock/pop, reggae), choix du tempo et lecture harmonique synthétique.
- **Répertoire** : fiches de morceaux avec tonalité, tempo et notes.
- **Tone Lab** : presets de sons avec guitare, ampli, pédales et réglages.
- **Sauvegarde** : export/import JSON des clés locales `ga3.*` et `ga2.*`, afin de préserver les favoris, l'historique, les accordages et les personnalisations déjà présents.

### Mise à jour depuis Guitar Atlas V3
1. Conserve une copie de sauvegarde de ton dossier V3.
2. Remplace les fichiers du site par ceux de ce paquet, en respectant le dossier `icons/`.
3. Le service worker utilise un nouveau cache `guitar-atlas-studio-v4.0.0` pour forcer la mise à jour des ressources.
4. Ouvre le site en ligne une fois. Si l'iPhone affiche encore l'ancienne version, ferme la PWA puis recharge le site dans Safari.
5. Avant toute manipulation de stockage, utilise l'onglet Studio > Sauvegarde pour exporter tes données.

### Limites de cette première extension
- Le Jam Studio joue une progression harmonique synthétique ; il ne contient pas encore de pistes batterie/basse réalistes ni un looper micro.
- Les grilles et morceaux sont enregistrés localement sur l'appareil. L'export JSON permet leur transfert manuel.
- Les fonctionnalités originales du dictionnaire, du manche, du tuner, du métronome et des personnalisations sont conservées dans leur code V3.
