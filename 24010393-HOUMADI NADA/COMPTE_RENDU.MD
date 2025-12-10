
<img src="NADA HOUMADI.jpg" style="height:264px;margin-right:264px"/>      <img src="ENCG SETTAT LOGO.png" style="height:264px;margin-right:264px"/>

**Étudiante : HOUMADI NADA**

**Module : Data Science **

# 📘 **Compte Rendu du Projet d’Analyse – Dataset DIABETES (Avec Problématique et Analyses Thématiques)**


---

## **📝 Problématique du Projet**

**Comment peut-on prédire la progression de la maladie diabétique à partir d’indicateurs physiologiques (BMI, pression sanguine, mesures sanguines) et quels sont les facteurs qui influencent le plus cette progression chez les patients ?**

Cette problématique vise à répondre à deux questions essentielles :

1. **Prédiction** : Peut-on estimer l’évolution de la maladie grâce au Machine Learning ?
2. **Compréhension** : Quels paramètres biologiques jouent un rôle majeur dans l’aggravation du diabète ?

---

## **1. Introduction Générale du Projet**

Ce projet vise à appliquer l'ensemble du cycle de vie d’un projet en Data Science sur un cas réel dans le domaine médical : la prédiction de la progression du diabète.
Grâce au dataset Diabetes de Scikit-Learn, nous cherchons à comprendre les facteurs qui influencent cette maladie chronique et à construire un modèle prédictif.

Cette étude est essentielle car elle permet :

* d’anticiper les complications,
* de cibler les patients à risque,
* d'aider à la prise de décision clinique.

---

## **2. Présentation du Jeu de Données**

Le dataset Diabetes contient :

* **442 patients**,
* **10 caractéristiques physiologiques**,
* 1 variable cible représentant la **progression du diabète**.

Les principales variables médicales analysées :

* **BMI** : surpoids/obésité, facteur majeur du diabète.
* **bp** : pression artérielle, souvent liée à des complications cardio-vasculaires.
* **s1–s6** : mesures sanguines (lipides, cholestérol, métabolisme du glucose).

---

## **3. Introduction et Nettoyage des Données Manquantes**

Pour simuler un contexte médical réel, 5 % de valeurs manquantes ont été introduites.
Elles ont ensuite été imputées par la moyenne, ce qui permet de conserver la structure et la taille du dataset.

---

## **4. Analyse Exploratoire et Compréhension Thématique**

### **4.1 Importance du BMI**

Un BMI élevé est fortement lié à une progression plus sévère du diabète.
Dans la littérature, le surpoids augmente la résistance à l’insuline, ce qui aggrave la maladie.

### **4.2 Indicateurs sanguins**

Les variables `s5` et `s6` sont fortement corrélées au target.
Elles pourraient représenter des marqueurs du métabolisme du glucose ou du cholestérol, très connectés au diabète.

### **4.3 Pression sanguine**

Une pression artérielle plus élevée indique une détérioration cardio-métabolique, souvent observée avec le diabète.

---

## **5. Préparation et Séparation des Données**

* 80 % pour l’entraînement
* 20 % pour le test
* Random_state fixé pour reproductibilité

---

## **6. Modélisation : Random Forest Regressor**

### Pourquoi Random Forest ?

* Capture les relations non linéaires (très présentes en biologie).
* Donne une mesure de l’importance des variables.
* Robuste face au bruit naturel des données médicales.

---

## **7. Résultats et Interprétation**

### **Performance du modèle**

* **R² ≈ 0.40**
* **RMSE ≈ 52**

### **Analyse**

* Le modèle explique 40 % de la progression du diabète.
* Logique, car de nombreux facteurs (alimentation, activité physique, génétique…) ne figurent pas dans le dataset.

### **Variables les plus importantes**

1. **BMI**
2. **s5** (marqueur sanguin lié au glucose)
3. **bp**
4. Autres variables sanguines

➡ Ces résultats confirment les connaissances médicales actuelles :
Le diabète est fortement influencé par **l’obésité** et **les biomarqueurs sanguins**.

---

## **8. Conclusion Générale**

Ce projet a permis de :

* comprendre les facteurs influençant la progression du diabète,
* construire un modèle prédictif fonctionnel,
* relier les résultats à la réalité médicale.

La problématique posée a été partiellement résolue :
✔ Oui, on peut prédire la progression du diabète.
✔ Oui, certains facteurs influencent plus que d’autres (BMI, s5, bp).
✖ Mais la prédiction reste limitée car d’autres facteurs manquent.

---

