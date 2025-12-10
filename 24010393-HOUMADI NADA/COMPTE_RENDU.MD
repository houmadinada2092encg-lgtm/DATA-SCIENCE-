

# 📘 **Compte Rendu du Projet d’Analyse – Dataset DIABETES (Version Enrichie avec Analyses Thématiques)**

**Étudiante : HOUMADI NADA**
**Module : Data Science – Cycle de Vie Complet**

---

## **1. Introduction Générale du Projet**

Ce projet a pour objectif d’explorer un dataset réel lié au **diabète**, une maladie chronique qui touche des millions de personnes dans le monde.
À travers l’analyse du dataset **Diabetes** de Scikit-Learn, nous cherchons à comprendre :

* quelles variables physiologiques influencent la progression de la maladie,
* comment détecter les facteurs à risque,
* et comment un modèle de Machine Learning peut aider à prédire l’évolution du diabète.

Ce type d’étude est fondamental en santé publique car il permet :

* d’identifier les patients à risque,
* d’améliorer le diagnostic,
* et de proposer des interventions plus adaptées.

---

## **2. Présentation du Jeu de Données et Théorie Médicale**

Le dataset contient 10 variables biologiques normalisées + une variable cible représentant la **progression de la maladie diabétique**.

Les variables importantes sur le plan médical :

### 🔹 **1. BMI (Indice de Masse Corporelle)**

Le BMI est un indicateur majeur, car l’obésité ou le surpoids sont des **facteurs aggravants du diabète de type 2**.
Une augmentation du BMI est fortement corrélée à une résistance à l’insuline.

### 🔹 **2. Blood Pressure (Pression Artérielle - bp)**

L’hypertension est souvent associée au diabète. Une augmentation de la pression sanguine peut indiquer une dégradation du système cardio-vasculaire.

### 🔹 **3. Variables sanguines (s1–s6)**

Elles représentent différentes concentrations biologiques liées :

* aux lipides,
* au cholestérol,
* au métabolisme du glucose.

Les variables `s5` et `s6` sont souvent considérées comme fortement liées à la régulation glycémique.

**L’objectif du projet : prédire la progression de la maladie à partir de ces facteurs.**

---

## **3. Traitement des Données Manquantes**

Une introduction artificielle de 5 % de données manquantes permet de simuler un contexte médical réel, où :

* des mesures peuvent être absentes,
* certaines analyses ne sont pas effectuées,
* des erreurs de laboratoire peuvent survenir.

L’imputation par la moyenne est correcte ici car :

* les variables sont continues,
* les données sont normalisées,
* cela évite de réduire la taille du dataset.

---

## **4. Analyse Exploratoire (EDA) – Compréhension Médicale**

### ### **4.1 Distribution du BMI**

L’analyse montre que les patients avec un IMC élevé présentent souvent une progression plus importante de la maladie.

→ **Interprétation clinique :**
L'obésité augmente la résistance à l’insuline, ce qui accélère l'évolution du diabète.

---

### **4.2 Corrélation entre les variables**

* La variable **s5** est fortement corrélée au target →
  Cela peut représenter un marqueur biologique très lié à l’évolution du diabète.

* Le BMI est également fortement corrélé →
  Confirmant qu’un poids élevé est un facteur aggravant.

* Certaines variables sanguines (s1, s2, s3) sont corrélées entre elles →
  Indiquant une **redondance biologique** (mêmes familles de lipides).

---

### **4.3 Variabilité de la progression du diabète**

La cible (`target`) varie fortement d’un patient à l’autre.
Cette variabilité traduit :

* les différences de mode de vie,
* le métabolisme personnel,
* la réponse individuelle au glucose.

---

## **5. Séparation Train/Test**

Une séparation 80/20 avec random_state=42 permet d’avoir :

* un entraînement fiable,
* une évaluation équitable.

---

## **6. Modélisation – Random Forest Regressor**

Le choix d’un **Random Forest** est très pertinent pour ce type de données car :

### ✔ **Il gère très bien les relations non linéaires (typique en biologie)**

Exemple : un BMI légèrement élevé n’a pas le même impact qu’un BMI très élevé.

### ✔ **Il peut capturer l’interaction entre plusieurs variables**

Exemple :
BMI **+** pression sanguine élevée → risque plus sévère.

### ✔ **Il fournit l’importance des variables**

Cela permet une interprétation médicale solide.

---

## **7. Analyse des Performances du Modèle**

### **Résultats obtenus :**

* **RMSE ≈ 52**
* **R² ≈ 0.40**

### **Interprétation médicale :**

Le modèle explique 40 % de la progression du diabète.
Cela peut paraître faible, mais il est important de noter que :

➡ le diabète dépend aussi de facteurs non inclus dans ce dataset :

* alimentation,
* activité physique,
* antécédents familiaux,
* prise de médicaments,
* stress,
* dynamique hormonale.

Donc **un modèle expliqué à 40 % est raisonnable dans ce contexte biomédical**.

---

## **8. Analyse des Variables Importantes**

Les résultats montrent que les variables les plus importantes sont :

### **1. BMI**

*Le facteur principal selon le modèle et la littérature scientifique.*

### **2. s5 (une mesure sanguine liée au métabolisme du glucose)**

Probablement un marqueur biologique très lié au risque diabétique.

### **3. Pression sanguine (bp)**

Indicateur majeur du risque cardio-métabolique.

### **4. Autres marqueurs sanguins**

Les variables s1 à s6 indiquent que **la composition sanguine est un facteur déterminant**.

➡ **Interprétation thématique globale :**
Le modèle montre que **le diabète est fortement influencé par l’obésité et par plusieurs indicateurs sanguins, ce qui confirme les connaissances médicales actuelles**.

---

## **9. Conclusion Générale**

Ce projet a permis d’appliquer l’ensemble du cycle Data Science sur un cas médical réel.
Les résultats obtenus mettent en évidence :

* le rôle majeur du BMI, déjà reconnu comme un facteur de risque,
* l’importance des marqueurs sanguins,
* une variabilité importante entre patients.

Le modèle Random Forest permet une prédiction correcte et une bonne compréhension des facteurs influents.

---



---


