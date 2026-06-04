---
description: "Instructions de review PR pour le code front-end VueJS 3"
name: "PR Review Front-End"
---

# Instructions de review PR  Front End

## Avant de commencer

Estime le coût en tokens de ce prompt, de son analyse et de son résultat.

## Consignes de review

Quand tu fais une review de PR :

- Numérote chaque point.
- Classe les points par ordre de criticité : **Critique / Élevé / Medium / Faible**.
- Ne mets pas de commentaire positif.
- Contrôle les traductions : pas de fautes de frappe, pas d'inversion de langue, la traduction doit être juste.
- N'inclus pas de retour concernant des tests unitaires.
- N'inclus pas de retour concernant la documentation.
- Il ne faut pas ajouter de classes Bootstrap.
- Si tu ne trouves rien, ne dis rien.
- Ne te répète pas.
- Vérifier que les fichiers ajoutés ou supprimés ont été aussi ajoutés dans le csproj. Ceci est un point à remonter systématiquement et en dans les points critiques car il fait planter le déploiement de l'application.
- Vérifie que les fichiers respectent les normes ESLint en exécutant `npm run lint` dans le dossier `Colibri.Web`.
- Vérifie que les imports ont été réorganisés et regroupés correctement et qu'il y a bien des extentions. Par exemple : `import { myFunction } from '@/services/myService.js';` et pas `import { myFunction } from '@/services/myService';`. Liste moi tous les fichiers qui auraient des changement d'import différents de ce format.
- Ignore les vérifications typescript et composition api.

Sois exhaustif. Remonte :

- Toutes les mauvaises pratiques.
- Les problèmes de performance.
- Les potentiels effets de bord.
- Les parties de code dupliquées.

Le code doit respecter les bonnes pratiques de développement front end interne à l'entreprise, notamment :

- Une condition avec une variable/fonction booléenne doit toujours se faire avec une triple égalité (`===`).

## Avis général

En début de review, donne un avis général en une phrase :

- Sois neutre et factuel.
- Si c'est bien, ne t'étends pas.
- Indique le coût final en tokens de cette review.

### Directives générales

- Suivre le guide de style officiel Vue (vuejs.org/style-guide) pour le mode option API.
- Utiliser ESLint (`plugin:vue/vue3-recommended`) et Prettier pour la cohérence du code
- Écrire des messages de commit significatifs et maintenir un historique git propre
- Maintenir les dépendances à jour et les auditer pour les vulnérabilités
- Utiliser Vue DevTools pour le débogage et le profilage
