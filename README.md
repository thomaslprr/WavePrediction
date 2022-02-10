# WavePrediction
Prédiction de la taille des vagues ainsi que de la période 🌊

## Problématique : Puis-je aller surfer ? 🏄
Étant surfeur, trois des critères les plus importants (à mon sens) pour savoir si les conditions sont optimales pour aller surfer sont : 

• Le vent 

• La taille des vagues

• La période

*Pour ce projet, le vent n'a pas été pris en compte car nous n'avions pas les données mais l'idée générale reste la même.*

**Objectif :** Je viens de me réveiller, il est 8h, il fait beau et je souhaite savoir si les conditions seront là pour surfer en fin de matinée aux alentours de 11h.
Vais-je pouvoir aller surfer ? 

--> Grâce au module développé je peux savoir si OUI ou NON je dois y aller. 

**Intérêt :** L'intérêt d'un tel modèle est d'éviter de me déplacer pour rien à la mer. Je ne veux pas faire 1h de route, charger tout mon matériel et arriver là-bas pour me rendre compte qu'aucune vague n'est présente.

## 📊 Jeu de données
Les données sont issues de Kaggle sous la licence : CC BY 4.0. 

Le jeu de données ressensent 30 mois de mesure à interval régulier (30 minutes) des données océaniques de Mooloolaba, ville cotière en Australie. 

Les mesures sont prises via une bouée flottante sur l'eau. 

|      **Info**              |    **Valeurs**        |
|--------------------|------------|
| Taille du fichier  | 2.15 Mo    |
| Nombre de lignes   | 43728      |
| Nombre de colonnes | 7          |
| Licence            | CC BY 4.0  |
| Durée des mesures  | 30 mois    |
| Interval de mesure | 30 minutes |

Les données pour se projet se trouvent [ici](https://www.kaggle.com/jolasa/waves-measuring-buoys-data-mooloolaba).

## 🖥️ Modèle
### Choix du modèle : ARIMA
Après plusieurs recherches du meilleur modèle à utiliser pour réaliser ce projet, j'ai décidé de partir sur le modèle ARIMA.

ARIMA est un modèle statistique pour analyser ou prédire les données de séries temporelles ou time series. Le principe est également connu sous l'appellation moyenne mobile autorégressive intégrée. (©journaldunet)

### Entraînement du modèle
Le modèle ARIMA a besoin de trois paramètres (p,d,q). Une première partie du projet a été dédié à trouver les meilleurs paramètres pour entraîner le modèle. 

Il existe deux principales techniques pour déterminer les valeurs : 

• Tester toutes les combinaisons raisonnables possibles 

• Etudier l'ACF et le PACF des données

J'ai opté pour la première solution même si j'ai également implémenté la deuxième solution pour comprendre de plus près le fonctionnement. 

### Utilisation du modèle
Une fois le modèle entraîné, j'ai décidé de l'utiliser dans deux cas d'usage. 

#### Prédiction à t+1 

Le premier consiste à prédire la prochaine étape (t+1). Autrement dit, le modèle est entraîné sur les données allant de la date x à la date y, on peut alors prédire facilement et précisement la date y+1 (qui correspond ici à 30 minutes après).

ARIMA est très précis pour effectuer ce type de prédiction et on obtient des résultats très satisfaisant. 

#### Prédiction à t+k

Ici, le but est de s'amuser avec le modèle et de l'utiliser dans un cadre bien plus semblable à la réalité. La prédiction à t+k permet de prédire non pas à l'étape t+1 (30 minutes) sinon t+k (k minutes dans le futur). Autrement dit, je ne souhaite pas connaître les conditions océaniques des 30 prochaines minutes mais celle dans 3 heures ou dans 24h. 

On peut effectuer différentes approches pour obtenir ce type de prédiction : 

• Prédire t+1 k fois en réentraînant le modèle à chaque fois 

• Prédire directement via le modèle le kième temps

J'ai choisi la deuxième option. Cette deuxième approche est plus simple à mettre en place mais donne des résultats moins performant. Cependant, le but de ce projet n'est pas forcément d'obtenir un modèle compétitif mais de découvrir les différentes possibilités et avoir un premier rendu satisfaisant. 

## Bilan

Au cours de ce projet, on a pu découvrir l'implémentation d'un modèle ARIMA et se rendre compte de l'intérêt d'un tel modèle. On se rend compte qu'on peut assez facilement, à partir de beaucoup de données, prédire un comportement naturel tel que l'évolution de la période des vagues ou de leur taille. 

