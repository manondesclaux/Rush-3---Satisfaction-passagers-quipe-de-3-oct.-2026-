# Rush 3 – Les 3M -  Satisfaction passagers 
## Contexte

Une compagnie aérienne européenne a interrogé plus de 100 000 passagers. Sa direction Expérience Client veut :

1. **savoir ce qui fait la satisfaction**, pour investir son budget là où il compte ;
2. **repérer les passagers probablement neutres ou insatisfaits avant leur sortie de l'aéroport**, pour que les équipes puissent les approcher. Les contraintes sont les suivantes : une approche coûte 40 €, et les équipes ne peuvent approcher qu'un passager sur dix.

## Principaux résultats

- 63 % des passagers sont neutres ou insatisfaits (avec l'hypothèse de répartition des classes Eco 55 %, Business 35 %, Eco Plus 10 %).
- **Où investir** : embarquement en ligne et wifi à bord, puis réservation en ligne. Il faut viser la note de 5 : une note « correcte » ne suffit pas.
- **Qui approcher** : les voyageurs de loisirs en Eco ou Eco Plus arrivés avec plus de 6 minutes de retard. 96 % d'entre eux sont neutres ou insatisfaits, et ils représentent environ 12 % des arrivées.
- **Modèle retenu** : un arbre de décision, explicable et sans âge ni genre. 96 % des passagers approchés sont réellement neutres ou insatisfaits, contre 90 % pour la meilleure règle simple et 63 % au hasard. Le gain net est d'environ 5 600 € pour 1 000 arrivées.

## Organisation du dépôt

```
.
├── rush3_final.ipynb        # LIVRABLE – code : nettoyage, analyse, modèles, évaluation finale
├── rapport_rush3.pdf        # LIVRABLE – rapport final (8 pages + 1 page d'annexes)
├── presentation_rush3.pptx  # LIVRABLE – support de la présentation orale (10 minutes)
│
├── data/                    # données fournies
│   ├── train.csv            # passagers de l'enquête : exploration, analyse et modèles
│   └── test.csv             # « passagers du mois suivant » : lus une seule fois, à la fin
├── scripts/
│   └── graphiques_rapport.py   # graphiques du rapport, appelés depuis le notebook
├── figures/                 # graphiques et tableaux produits par le notebook
├── fonts/                   # police IBM Plex Sans (licence OFL), utilisée par les graphiques
└── docs/
    └── README.md            # ce fichier
```

## Reproduire les résultats

```bash
pip install numpy==2.0.2 pandas==2.3.3 matplotlib==3.9.4 scikit-learn==1.6.1 jupyter
jupyter notebook rush3_final.ipynb
```

Lancer ces commandes depuis la **racine du dépôt** (le notebook lit `data/` et importe `scripts/graphiques_rapport.py`), puis exécuter le notebook du début à la fin (« Restart & Run All »).

- Versions utilisées : Python 3.9.6, numpy 2.0.2, pandas 2.3.3, matplotlib 3.9.4, scikit-learn 1.6.1.
- Le hasard est fixé (graine 42) : deux exécutions donnent exactement les mêmes chiffres.
- Tous les chiffres et graphiques du rapport sont produits par le notebook et par `scripts/graphiques_rapport.py`, dans le dossier `figures/`.

## Règles du sujet respectées

- **Le fichier test n'est lu qu'une seule fois**, dans la dernière section du notebook, derrière le verrou `RUN_FINAL_TEST` et sur le modèle déjà choisi. Il n'a servi ni à explorer les données, ni à choisir les variables, ni à régler le modèle.
- **Les modèles sont comparés par validation croisée** (5 parts) sur le fichier d'entraînement uniquement.
- **Le modèle n'utilise que des informations connues à l'atterrissage** : classe, motif du voyage déclaré, fidélité, retard à l'arrivée, distance. Les notes du questionnaire, l'âge et le genre ne sont pas utilisés.
- **Deux approches de classification au moins** (arbre de décision, gradient boosting, régression logistique) sont comparées à la règle la plus simple applicable sans modèle.

## Livrables attendus

| Livrable | Contenu | Emplacement |
|---|---|---|
| Rapport PDF (8 pages maximum, hors annexes) | Synthèse d'une page pour la direction, exploration, facteurs de satisfaction, modèles, recommandations, protection des données | `rapport_rush3.pdf` |
| Code | Notebook et script qui reproduisent chaque chiffre et chaque graphique du rapport | `rush3_final.ipynb` (et `scripts/graphiques_rapport.py`, appelé par le notebook) |
| Présentation orale | 10 minutes devant la direction, suivies de questions sur nos choix d'analyse | `presentation_rush3.pptx` |
| Dépôt Git | Historique montrant le partage du travail ; README indiquant qui a fait quoi | Ce dépôt |

## Répartition des tâches

L'équipe : **Mina**, **Manon D.** et **Manon R.**

Le travail a été réparti **à parts égales** entre les trois membres. Chacune a participé à toutes les étapes ci-dessous.

| Étape | Contenu | Réalisé par |
|---|---|---|
| Traitement des données | Chargement et contrôle qualité, retrait de l'identifiant et des 310 retards manquants, traitement des notes de 0, correction de l'écart de sondage entre classes, exploration (motif, classe, âge, distance, retard) | Mina, Manon D., Manon R. |
| Facteurs de satisfaction | Lien note / satisfaction par classe (corrélation de Spearman), effet à profil égal (régression logistique), analyse « note 3 contre note 5 », distinction association / levier / cause | Mina, Manon D., Manon R. |
| Modélisation | Règles de référence, arbre de décision, gradient boosting, régression logistique, validation croisée, coût des erreurs, choix du modèle, évaluation finale sur le fichier test, profils types | Mina, Manon D., Manon R. |
| Réflexion RGPD | Nouvel usage des données, conditions d'acceptabilité (analyse d'impact, information, droit d'opposition), choix de chaque variable, cas des mineurs, ce que voit l'agent | Mina, Manon D., Manon R. |
| Rapport PDF | Structure, rédaction pour un directeur non spécialiste, graphiques, recommandations | Mina, Manon D., Manon R. |
| Présentation PowerPoint | Support de l'oral de 10 minutes et préparation des questions | Mina, Manon D., Manon R. |
| Code et dépôt | Notebook, script des graphiques, reproductibilité, organisation du dépôt, README | Mina, Manon D., Manon R. |
