# Spotify Radar

Outil local pour :
- **Artistes non suivis** : choisir une de tes playlists et voir les artistes que tu ne suis pas (bouton « Suivre »).
- **Découvrir** : trouver les titres des artistes d'une playlist que tu n'as ni likés ni dans tes playlists, plus des titres d'artistes proches (par genre).
- **Nouveautés** : les albums/singles sortis récemment chez tes artistes suivis (7 à 60 jours).

## Installation (5 min, une seule fois)

1. Va sur https://developer.spotify.com/dashboard (compte **Premium** requis par Spotify depuis 2026).
2. **Create app** → nom libre, cocher *Web API*.
3. Redirect URI : `https://natouu444.github.io/spotify-radar/` (ou `http://127.0.0.1:8888/` en local).
4. Copie le **Client ID**.

## Lancement

Dans le dossier contenant `index.html` :

```bash
python3 -m http.server 8888 --bind 127.0.0.1
```

Puis ouvre http://127.0.0.1:8888/ dans ton navigateur, colle le Client ID et connecte-toi.

## Limites (imposées par Spotify, pas par l'outil)

- Seules les playlists dont tu es propriétaire (ou collaboratives) sont lisibles. Celles de Spotify (Discover Weekly, etc.) ou d'autres utilisateurs : 🔒. Astuce : copie-les dans une playlist à toi.
- Spotify a supprimé les endpoints « nouvelles sorties », « recommandations » et « artistes similaires » : l'outil les remplace par le scan des albums de tes artistes suivis et une recherche par genre.
- Le scan des nouveautés fait un appel par artiste suivi : quelques minutes si tu en suis des centaines (les limites de débit sont gérées automatiquement).
