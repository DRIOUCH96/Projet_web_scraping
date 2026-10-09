# Projet de collecte web responsable

Ce dépôt contient les trois notebooks complétés du brief : collecte de livres,
prise en compte du `User-Agent` et de `robots.txt`, puis adaptation de la méthode
à un second site d'entraînement.

## Ordre d'exécution

1. `1-scraping-classique.ipynb` collecte les 1 000 livres et crée `livres.csv`.
2. `2-user-agent-et-robots-enonce.ipynb` compare les requêtes, interprète
   `robots.txt` et mesure une collecte avec pause et nouvelle tentative.
3. `3-mission-adaptation-enonce.ipynb` collecte les citations et une seule fiche
   par auteur, puis réalise la fusion et les classements demandés.

Exécuter les cellules de chaque notebook dans l'ordre, depuis ce dossier, afin
que les fichiers CSV soient enregistrés au bon endroit.

## Installation

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m notebook
```

Le paquet `truststore` est utilisé de manière optionnelle pour les postes
Windows dont Python ne retrouve pas correctement les certificats du système.
La vérification HTTPS n'est jamais désactivée.

## Contrôles attendus

- `livres.csv` contient 1 000 lignes et des UPC uniques ;
- les descriptions absentes restent des valeurs manquantes sans interrompre le
  traitement ;
- la collecte classique envoie 50 requêtes de pagination et 1 000 requêtes de
  détail ;
- le `User-Agent` contient un contact public et les règles `robots.txt` sont
  testées avant la collecte responsable ;
- les codes 429 et 503 déclenchent des tentatives espacées ;
- la mission d'adaptation collecte 100 citations et ne demande chaque fiche
  d'auteur qu'une fois.

Le contact public configuré est `https://github.com/DRIOUCH96`. Il peut être
modifié via la variable `CONTACT` dans les notebooks 2 et 3.

## Limite du brief

La situation professionnelle mentionne l'entraînement d'un modèle
d'apprentissage profond. Les notebooks fournis, les livrables et les critères
d'évaluation portent toutefois uniquement sur la collecte web. Aucun jeu de
cibles, objectif de prédiction ou protocole d'évaluation de modèle n'est défini ;
ce volet doit donc faire l'objet d'un brief complémentaire avant implémentation.
