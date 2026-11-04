# TD GitHub Actions — Rendu

**Dépôt :** https://github.com/leo-grnd/td-actions-Leo-Dorian/
**Site en ligne :** 

## Question 1

Le commit qui cassait la page (suppression de `</body>`) est-il encore dans
l'historique de `main` ? Pourquoi la vérification ne l'a-t-elle pas empêché
d'y entrer ?

**Réponse :** Oui, ce commit est toujours présent dans l'historique de `main`
(visible dans `git log`). La vérification ne l'a pas empêché d'entrer car, à
ce moment du TD, aucune protection de branche n'était encore en place sur
`main`. Le workflow se déclenche sur `push` : il observe un commit après
qu'il est déjà entré sur la branche, il ne peut rien bloquer avant. Seule la
protection de branche ajoutée à l'étape 5 (avec le contrôle de statut
obligatoire) empêche une fusion si la vérification échoue.

## Question 2

Deux workflows existent (`Verification` et `Deploy static content to
Pages`). Lesquels se déclenchent sur un push vers `main`, et dans quel ordre
se terminent-ils ?

**Réponse :** Les deux se déclenchent sur un push vers `main` (tous deux ont
un déclencheur `push: branches: [main]`).

## Grille d'autocontrôle

| Fait | Ce qui est attendu |
|---|---|
| ✅ | Le dépôt est public et contient `index.html` et `style.css` |
| ✅ | `.github/workflows/verification.yml` existe et sa dernière exécution est verte |
| ✅ | Le workflow se déclenche sur `push` et sur `pull_request` |
| ✅ | Une pull request a été ouverte, vérifiée, relue puis fusionnée (PR #1) |
| ✅ | La branche `main` refuse une fusion dont la vérification est rouge (testé avec la PR #2, fermée sans fusion) |
| ✅ | Le site est en ligne et son URL fonctionne |
| ✅ | binôme A/B |
| ✅ | Les réponses aux questions 1 et 2 sont écrites ci-dessus |

Le point 7 (revue croisée avec un autre binôme) n'a pas pu être réalisé :
il suppose un échange avec une équipe externe réelle.
