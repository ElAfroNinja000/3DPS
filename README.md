# 3DPS

**45,000 Spotify tracks, clustered on eight audio features and projected into 3D. Fly through the cloud, hover a sphere to read the track, click it to play.**

![Three.js](https://img.shields.io/badge/three.js-000000?style=for-the-badge&logo=threedotjs&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-990000?style=for-the-badge&logo=webgl&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Spotify](https://img.shields.io/badge/Spotify-1DB954?style=for-the-badge&logo=spotify&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)

---

## What it is

Music similarity is usually served as a list. 3DPS turns it into a space you can move through.

Every sphere is one track. Its position comes from Spotify audio features: danceability, energy, valence, acousticness, instrumentalness, liveness, speechiness and tempo.
These features are then used to compute 3D coordinates using UMAP. Tracks that sound alike end up near each other, so the clusters emerge from the audio itself.

Then you fly through it. Hover a sphere and the track surfaces. Click and it plays.
Whenever you select a sphere, it gets added to your history. You can also add songs to your favorites.

## How it works

```
spotify_data/spotify_raw_data.csv
        ↓
  cleaning & completion  →  clustering  →  UMAP projection (8D → 3D)
        ↓
   static JSON  →  Three.js renderer
```

The Python side (`scripts/`) reads a raw Spotify export from `spotify_data/spotify_raw_data.csv`, completes and clusters it, then projects it down to three dimensions and writes a static JSON.

## Try it

Visit **→ [www.samy-abdelazim.com](https://www.samy-abdelazim.com)** and scroll to 3DPS and hit *Launch experience*.

## Work in progress

3DPS is a learning project and needs to be developed even more. Here's a list of the major changes I have in mind:

- **Ingestion still starts from a static CSV.** Everything downstream is automated, but the source is a one-off export sitting in `spotify_data/`. Wiring it to the Spotify API directly would make the cloud refreshable instead of frozen.
- **The point count is hard-coded** in the processing scripts. Resizing the cloud means editing a constant rather than passing a parameter.

## Credits

Audio features from the [Spotify Web API](https://developer.spotify.com/documentation/web-api). Projection with [UMAP](https://umap-learn.readthedocs.io/). Rendering with [Three.js](https://threejs.org/).

Built by [Samy Abdelazim](https://www.samy-abdelazim.com)
