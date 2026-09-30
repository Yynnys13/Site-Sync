# CSS

## Où trouver les CSS
Le chemin distant est reproduit tel quel sous `site/` :

```
https://example.com/assets/css/main.css   →   site/assets/css/main.css
```

Les CSS apparaissent aussi dans la vue **Ressources › CSS** de Site Sync (clic = ouvrir).

## Modifier un CSS
1. Ouvrez le fichier CSS.
2. Modifiez le code.
3. Sauvegardez (`Ctrl + S`).
4. Site Sync détecte la modification (après un court *debounce* de 150 ms).
5. La preview applique le nouveau CSS.

## Live Reload
Le CSS est mis à jour **à chaud** : la balise `<link rel="stylesheet">` correspondante est remplacée par une copie rechargée, puis l'ancienne est retirée. La page ne se recharge pas, l'état JS et le scroll sont conservés.

> **Limites** — Si le CSS n'est pas référencé par une balise `<link>` (par exemple un `@import` dans un autre CSS, ou un `<style>` inline), la page est rechargée entièrement. Les CSS injectés dynamiquement par JavaScript suivent la même règle.

Les `url(...)` et `@import` absolus vers votre domaine sont ramenés dans le proxy ; ceux vers un CDN passent par `/__ss_ext/…` afin d'être eux aussi interceptés.
