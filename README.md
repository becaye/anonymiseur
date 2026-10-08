# Anonymiseur local

Outil web d'anonymisation de textes et d'extraits HTML qui fonctionne **entièrement dans le navigateur**. Aucune donnée n'est envoyée sur le réseau.

**[Utiliser l'outil](https://VOTRE-COMPTE.github.io/anonymiseur/)**

## Fonctionnement

1. **Source** : collez un texte ou un extrait de code HTML.
2. **Détection** : choisissez les détecteurs automatiques, complétez le dictionnaire de termes et la liste d'exclusions.
3. **Revue** : vérifiez chaque donnée repérée, ignorez les faux positifs, ajoutez les oublis, ajustez les remplacements.
4. **Export** : copiez ou téléchargez le résultat, et si besoin la table de correspondance.

### Détecteurs automatiques

Adresses e-mail, URL, numéros de téléphone français, IBAN (clé vérifiée), cartes bancaires (contrôle de Luhn), numéros de sécurité sociale, SIREN/SIRET (contrôle de Luhn), adresses IP, adresses postales, noms précédés d'une civilité, « Prénom NOM » en capitales, dates.

Un nom repéré une seule fois est ensuite recherché dans tout le contenu.

### Mode HTML

Seuls les nœuds texte, les commentaires et une liste configurable d'attributs (`alt`, `title`, `value`, `aria-label`, `href`…) sont modifiés. Les balises, `id`, classes, `role` et relations ARIA (`aria-labelledby`, `aria-describedby`…) restent intacts, ainsi que le contenu des balises `script` et `style`. Le reste du code est conservé à l'identique.

### Stratégies de remplacement

- Étiquettes numérotées : `[NOM_1]`, `[EMAIL_2]`…
- Valeurs fictives : `Personne A`, `personne1@exemple.fr`, `192.0.2.1`…
- Masquage : `█████`

## Confidentialité

- La page déclare une politique de sécurité de contenu (`connect-src 'none'`, `default-src 'none'`) : le navigateur bloque toute requête réseau émise par la page. Un indicateur en haut de page confirme que ce blocage est actif.
- Aucune bibliothèque externe, aucune police distante, aucun outil de mesure d'audience.
- Vous pouvez le vérifier dans l'onglet Réseau des outils de développement : après le chargement initial, aucune requête ne doit apparaître.
- Pour les contenus sensibles, vous pouvez télécharger `index.html` et l'ouvrir en local, sans connexion.

La table de correspondance contient les données d'origine : avec elle, le résultat est une **pseudonymisation** au sens du RGPD, pas une anonymisation.

## Limites

- Les détecteurs visent les formats français.
- Les noms sans civilité ni capitales ne sont repérés que par le dictionnaire ou l'ajout manuel.
- Les identifiants indirects (fonction unique, anecdote, combinaison lieu et date) ne sont pas détectés : une relecture humaine reste indispensable.
- En mode HTML, les entités encodées (`&eacute;`…) ne sont pas décodées avant la recherche.

## Licence

MIT, voir [LICENSE](LICENSE).
