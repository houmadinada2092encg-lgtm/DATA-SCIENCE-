

# 📘 **Compte Rendu du Projet d’Analyse – Dataset DIABETES**

**Étudiante : HOUMADI NADA**
**Module : Data Science – Cycle de Vie Complet**

---

## **1. Introduction Générale du Projet**

Ce projet s’inscrit dans le cadre de l’évaluation continue en Data Science. L’objectif principal était de mettre en œuvre le cycle complet d’un projet analytique : chargement, nettoyage, exploration, modélisation et évaluation.
Le dataset utilisé est **Diabetes**, fourni par Scikit-Learn, et vise à **prédire la progression quantitative de la maladie diabétique** à partir de variables physiologiques.

Ce travail permet de mobiliser les compétences essentielles abordées en cours : manipulation des données, statistiques, visualisation, Machine Learning et interprétation des résultats.

---

## **2. Description du Jeu de Données**

Le dataset contient :

* **442 observations**,
* **10 variables explicatives continues**,
* une variable cible : **target** (évolution de la maladie).

Les variables principales incluent :

* **age** : âge normalisé
* **bmi** : indice de masse corporelle
* **bp** : pression sanguine
* **s1 à s6** : mesures sanguines

L’objectif du projet est d’expliquer la progression du diabète à partir de ces indicateurs.

---

## **3. Introduction et Traitement des Données Manquantes**

Pour simuler un contexte réel, 5 % de valeurs manquantes ont été introduites artificiellement dans toutes les variables d’entrée.
Afin de nettoyer ces données, une imputation par la **moyenne** a été réalisée grâce à `SimpleImputer`.

* Cette méthode est adaptée aux variables numériques continues.
* Elle permet de conserver l’intégralité du dataset.
* À la fin du nettoyage : **aucune valeur manquante restante**.

---

## **4. Analyse Exploratoire (EDA)**

### **4.1 Statistiques descriptives**

Les statistiques montrent que les variables sont normalisées, ce qui facilite les comparaisons et l’entraînement du modèle.

### **4.2 Analyse de la variable BMI**

Un histogramme a montré que les valeurs élevées du BMI sont souvent associées à une progression plus grave du diabète.

### **4.3 Matrice de corrélation**

La heatmap révèle :

* une corrélation forte entre `s5` et la progression du diabète,
* un rôle important du `bmi`,
* plusieurs corrélations entre indicateurs sanguins, indiquant une redondance partielle.

---

## **5. Préparation et Séparation des Données**

Les données propres ont été séparées :

* **80 % pour l’entraînement**,
* **20 % pour le test**,
  avec un `random_state=42` pour garantir la reproductibilité.

Cette étape assure une évaluation objective du modèle.

---

## **6. Modélisation : Random Forest Regressor**

Le modèle choisi est un **Random Forest** avec 100 arbres.
Ce choix est justifié par :

* sa robustesse face au bruit,
* sa capacité à modéliser des relations non linéaires,
* son efficacité sur les datasets de taille réduite.

Le modèle a été entraîné sur les données nettoyées et prêtes à l’emploi.

---

## **7. Évaluation du Modèle**

### **7.1 Résultats obtenus**

* **RMSE : ~52.00**
* **R² Score : ~0.40**

### **7.2 Interprétation**

* Le modèle explique environ **40 %** de la variabilité du target.
* Le RMSE indique un écart moyen de 52 unités entre prédictions et valeurs réelles.
* Ces performances sont cohérentes avec la nature complexe et bruitée du dataset.

### **7.3 Analyse des résidus**

* Résidus centrés autour de 0 → bon signe.
* Dispersion importante → difficulté à capturer toute la complexité médicale.

### **7.4 Importance des variables**

Les variables les plus explicatives sont :

1. **bmi**
2. **s5**
3. **bp**
   Les mesures sanguines jouent également un rôle clé.

---

## **8. Conclusion Générale**

Ce projet a permis de développer un pipeline complet :
**Chargement → Nettoyage → Analyse → Modélisation → Interprétation**.

Les résultats montrent que certains facteurs — notamment le BMI et les indicateurs sanguins — influencent fortement la progression du diabète.
Le modèle Random Forest, bien que performant, pourrait être amélioré via une optimisation des hyperparamètres ou des modèles alternatifs.

---

## **9. Perspectives d’Amélioration**

* Utilisation de GridSearchCV pour optimiser les paramètres.
* Comparaison avec d’autres modèles (régression linéaire, Ridge, XGBoost).
* Réduction de dimension via PCA pour traiter la redondance entre variables sanguines.
* Ajout de nouvelles variables dérivées (features engineering).

---


