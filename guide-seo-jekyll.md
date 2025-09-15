# 📈 Guide SEO pour Jekyll sur GitHub Pages

Avec le plugin `jekyll-seo-tag` sur GitHub Pages,    
voici un plan pour améliorer ton référencement naturel (SEO).

---

## 1. Configurer `_config.yml`

Ajoute toutes les métadonnées utiles et active les plugins supportés par GitHub Pages.

```yml
title: Mon super site
description: Tutoriels et notes sur X
url: https://mon-domaine.fr        # ou https://user.github.io/mon-repo
baseurl: ""                        # ou "/mon-repo" si projet
lang: fr
timezone: Europe/Paris

author:
  name: Prénom Nom
  email: moi@example.com
  url: https://mon-domaine.fr/a-propos

logo: /assets/img/logo.png

social:
  name: Mon Site
  links:
    - https://github.com/mon-user
    - https://www.linkedin.com/in/mon-profil/

plugins:
  - jekyll-seo-tag
  - jekyll-sitemap
  - jekyll-feed
  - jekyll-redirect-from

permalink: /:categories/:title/
```

---

## 2. Soigner le front matter des pages

Chaque page doit avoir ses propres métadonnées uniques.

```yaml
---
layout: default
title: "Titre clair avec mot-clé"
description: "Résumé en 150–160 caractères, naturel et unique."
image: /assets/img/og/ma-page.png
last_modified_at: 2025-09-10
lang: fr
---
```

---

## 3. Ajuster le layout

- Garde **un seul `<h1>`** par page.  
- Utilise des `<h2>` et `<h3>` dans le contenu.  
- Ajoute un **fil d'Ariane** si tu as des catégories.  
- Vérifie que toutes les images ont un `alt` descriptif et des dimensions.  

Tu peux ajouter dans `<head>` :

```html
<link rel="alternate" type="application/rss+xml" href="{{ '/feed.xml' | relative_url }}">
```

---

## 4. Contenu & maillage interne

- Une **page = une intention de recherche**.  
- Viser **500–1200 mots** utiles, bien structurés.  
- Ajouter **liens internes** vers d'autres pages pertinentes.  
- Ajouter quelques **liens externes** fiables.  

---

## 5. Performance & Core Web Vitals

- Compresser/minifier CSS/JS.  
- Utiliser des images **WebP** avec `srcset`.  
- Activer **HTTPS** dans les paramètres GitHub Pages.  
- Utiliser un **domaine custom** avec `CNAME`.  

---

## 6. Fichiers SEO à la racine

`robots.txt` :

```txt
User-agent: *
Allow: /
Sitemap: https://mon-domaine.fr/sitemap.xml
```

`404.html` : page personnalisée avec liens utiles.

---

## 7. Multilingue

- Si site **mono-langue** : `lang: fr` suffit.  
- Si **multi-langue** : utiliser `/fr/`, `/en/` et ajouter `hreflang`.  

---

## 8. Données structurées

`jekyll-seo-tag` ajoute déjà du JSON-LD de base.  
Pour un article riche :

```html
<script type="application/ld+json">
{
  "@context":"https://schema.org",
  "@type":"Article",
  "headline":"{{ page.title | escape }}",
  "description":"{{ page.description | escape }}",
  "image":"{{ site.url }}{{ page.image }}",
  "author":{"@type":"Person","name":"{{ site.author.name }}"},
  "datePublished":"{{ page.date | date_to_xmlschema }}",
  "dateModified":"{{ page.last_modified_at | date_to_xmlschema }}"
}
</script>
```

---

## 9. Redirections propres

Si tu changes une URL :

```yaml
---
redirect_from:
  - /ancienne-url/
---
```

---

## 10. Check-list avant publication ✅

- [ ] Chaque page a **title** + **description** uniques  
- [ ] Une **H1** unique par page  
- [ ] Hiérarchie **H2/H3** logique  
- [ ] Images avec **alt**, **width/height**, **WebP** si possible  
- [ ] Liens internes vers 2–3 pages pertinentes  
- [ ] `last_modified_at` mis à jour  
- [ ] `sitemap.xml` et `robots.txt` accessibles  
- [ ] Pages test ou brouillon avec `<meta name="robots" content="noindex">`

---

👉 Avec ça, tu as une base SEO solide sur GitHub Pages.
