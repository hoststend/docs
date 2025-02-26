---
name: distance-coordinates
---
**GET** `/test/distance-coordinates`

## Paramètres

Query : `?latitude1=...&longitude1=...&latitude2=...&longitude2=...`

- `latitude1` : latitude de la première coordonnée, la virgule étant représentée par un point
- `longitude1` : longitude de la première coordonnée, la virgule étant représentée par un point
- `latitude2` : latitude de la deuxième coordonnée, la virgule étant représentée par un point
- `longitude2` : longitude de la deuxième coordonnée, la virgule étant représentée par un point

## Authentification

Aucune.

## Réponse

```json
{
  "distance": 1.0 // en km
}
```
