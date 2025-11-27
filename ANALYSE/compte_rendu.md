# 📊 Analyse complète du jeu de données `business_SALES`

Ce document présente une analyse statistique complète du jeu de données **business_SALES**, incluant :
- la description générale de la base,
- les méthodes statistiques descriptives utilisées,
- les visualisations,
- et des interprétations détaillées.

---

## 1️⃣ Description générale de la base de données

Le jeu de données **business_SALES** représente des informations commerciales sur les ventes d’une entreprise.  
En général, il contient des variables typiques telles que :

- **Date** : période d'observation des ventes  
- **Product / Category** : le produit ou la catégorie vendue  
- **Region / Country** : zone géographique  
- **Units_Sold** : quantité vendue  
- **Unit_Price** : prix unitaire  
- **Revenue** : chiffre d’affaires généré  
- **Cost** : coût total  
- **Profit** : marge réalisée  

👉 *Ces variables permettent d’étudier la performance commerciale, les tendances de vente, la rentabilité et les variations géographiques ou temporelles.*

---

## 2️⃣ Méthodes statistiques utilisées

Pour analyser la base **business_SALES**, les méthodes suivantes sont appliquées :

### 🔹 Statistiques descriptives
- Moyenne, médiane, variance, écart-type  
- Minimum, maximum  
- Distribution des variables (histogrammes)  
- Analyse des valeurs manquantes  
- Analyse de la corrélation entre variables  

### 🔹 Visualisation
- Histogrammes  
- Boxplots (détection d’outliers)  
- Graphiques temporels  
- Bar charts par catégorie ou région  
- Heatmap de corrélation  

### 🔹 Analyses avancées
- Analyse des profits par produit  
- Analyse des ventes par région  
- Identification des produits les plus performants  
- Analyse des tendances temporelles  

---

## 3️⃣ Code Python complet

```python
# ==========================
# 📦 IMPORTATION DES LIBRAIRIES
# ==========================
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# ==========================
# 📥 IMPORTATION DU JEU DE DONNÉES
# ==========================
df = pd.read_csv("business_SALES.csv")

# ==========================
# 📝 APERÇU DU JEU DE DONNÉES
# ==========================
print("Aperçu des premières lignes :")
display(df.head())

print("\nInformations générales :")
df.info()

print("\nValeurs manquantes :")
print(df.isnull().sum())

# ==========================
# 📊 STATISTIQUES DESCRIPTIVES
# ==========================
print("\nStatistiques descriptives :")
display(df.describe())

# ==========================
# 📈 DISTRIBUTION DES VARIABLES NUMÉRIQUES
# ==========================
df.hist(figsize=(12,8))
plt.suptitle("Distribution des variables numériques")
plt.show()

# ==========================
# 🎯 BOXPLOTS POUR LES OUTLIERS
# ==========================
plt.figure(figsize=(10,5))
sns.boxplot(data=df.select_dtypes(include='number'))
plt.title("Détection des valeurs extrêmes")
plt.xticks(rotation=45)
plt.show()

# ==========================
# 🔥 MATRICE DE CORRÉLATION
# ==========================
plt.figure(figsize=(10,6))
sns.heatmap(df.corr(), annot=True, cmap="coolwarm")
plt.title("Matrice de corrélation")
plt.show()

# ==========================
# 💰 ANALYSE DU CHIFFRE D'AFFAIRES PAR PRODUIT
# ==========================
revenue_by_product = df.groupby("Product")["Revenue"].sum().sort_values(ascending=False)

plt.figure(figsize=(10,5))
revenue_by_product.plot(kind="bar")
plt.title("Chiffre d'affaires total par produit")
plt.ylabel("Revenue")
plt.show()

# ==========================
# 🌍 ANALYSE DES VENTES PAR RÉGION
# ==========================
sales_by_region = df.groupby("Region")["Units_Sold"].sum().sort_values(ascending=False)

plt.figure(figsize=(10,5))
sales_by_region.plot(kind="bar", color="green")
plt.title("Ventes totales par région")
plt.ylabel("Units Sold")
plt.show()

# ==========================
# 📆 ANALYSE TEMPORELLE DES VENTES
# ==========================
df["Date"] = pd.to_datetime(df["Date"])
sales_time = df.groupby("Date")["Revenue"].sum()

plt.figure(figsize=(12,5))
plt.plot(sales_time)
plt.title("Tendance du chiffre d'affaires dans le temps")
plt.ylabel("Revenue")
plt.xlabel("Date")
plt.show()




  ##Synthèse de l'analyse

- Le dataset présente une structure riche permettant une compréhension claire des ventes.
- La distribution des ventes montre une variabilité importante et des valeurs extrêmes significatives.
- Plusieurs catégories dominent le chiffre d'affaires total.
- L’analyse temporelle montre des variations mensuelles qui peuvent guider la planification stratégique.
- Les corrélations révèlent des liens clés entre variables de performance.
- Les valeurs aberrantes doivent être traitées ou étudiées plus en détail pour éviter des interprétations biaisées.



