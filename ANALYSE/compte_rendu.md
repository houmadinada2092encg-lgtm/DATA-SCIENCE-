# -------------------------------------------------------------
# 📊 ANALYSE COMPLETE DU JEU DE DONNÉES BUSINESS_SALES
# -------------------------------------------------------------

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# -------------------------------------------------------------
# 1. IMPORTATION DES DONNÉES
# -------------------------------------------------------------
df = pd.read_csv("Business_SALES.csv")   # Modifiez le nom si différent
print("Aperçu des données :")
print(df.head())


# -------------------------------------------------------------
# 2. DESCRIPTION GENERALE DU DATASET
# -------------------------------------------------------------
print("\n--- Informations générales ---")
print(df.info())

print("\n--- Statistiques descriptives ---")
print(df.describe(include='all').T)

print("\n--- Valeurs manquantes par colonne ---")
print(df.isnull().sum())


# -------------------------------------------------------------
# 3. STATISTIQUES DESCRIPTIVES DETAILLEES
# -------------------------------------------------------------
stats = df.describe(include='all').T
print("\n--- Statistiques détaillées ---")
print(stats)


# -------------------------------------------------------------
# 4. ANALYSE DE LA VARIABLE DES VENTES (Sales)
# -------------------------------------------------------------
if "Sales" in df.columns:
    plt.figure(figsize=(8,5))
    plt.hist(df["Sales"].dropna(), bins=20)
    plt.title("Distribution des ventes")
    plt.xlabel("Montant des ventes")
    plt.ylabel("Fréquence")
    plt.show()


# -------------------------------------------------------------
# 5. ANALYSE PAR CATEGORIE (Category)
# -------------------------------------------------------------
if "Category" in df.columns and "Sales" in df.columns:
    print("\n--- Total des ventes par catégorie ---")
    print(df.groupby("Category")["Sales"].sum().sort_values(ascending=False))

    print("\n--- Moyenne des ventes par catégorie ---")
    print(df.groupby("Category")["Sales"].mean().sort_values(ascending=False))


# -------------------------------------------------------------
# 6. GRAPHIQUE : VENTES PAR CATEGORIE
# -------------------------------------------------------------
if "Category" in df.columns and "Sales" in df.columns:
    plt.figure(figsize=(10,6))
    df.groupby("Category")["Sales"].sum().plot(kind="bar")
    plt.title("Ventes totales par catégorie")
    plt.xlabel("Catégorie")
    plt.ylabel("Total des ventes")
    plt.show()


# -------------------------------------------------------------
# 7. ANALYSE TEMPORELLE (si une colonne Date existe)
# -------------------------------------------------------------
if "Date" in df.columns:
    df["Date"] = pd.to_datetime(df["Date"], errors='coerce')
    df = df.set_index("Date")

    plt.figure(figsize=(12,6))
    df["Sales"].resample("M").sum().plot()
    plt.title("Évolution mensuelle des ventes")
    plt.xlabel("Date")
    plt.ylabel("Ventes mensuelles")
    plt.show()


# -------------------------------------------------------------
# 8. MATRICE DE CORRELATION
# -------------------------------------------------------------
plt.figure(figsize=(8,6))
corr = df.corr(numeric_only=True)
plt.matshow(corr, fignum=1)
plt.colorbar()
plt.title("Matrice de corrélation")
plt.show()

print("\n--- Corrélations ---")
print(corr)


# -------------------------------------------------------------
# 9. DETECTION DES OUTLIERS
# -------------------------------------------------------------
if "Sales" in df.columns:
    Q1 = df["Sales"].quantile(0.25)
    Q3 = df["Sales"].quantile(0.75)
    IQR = Q3 - Q1

    outliers = df[(df["Sales"] < Q1 - 1.5 * IQR) |
                  (df["Sales"] > Q3 + 1.5 * IQR)]

    print("\n--- Outliers détectés dans Sales ---")
    print(outliers.head())


# -------------------------------------------------------------
# 10. CONCLUSION AUTOMATIQUE
# -------------------------------------------------------------
print("\n-------------------------------------------------------")
print("RÉSUMÉ AUTOMATIQUE DE L’ANALYSE")
print("-------------------------------------------------------")

print(f"- Nombre d'observations : {df.shape[0]}")
print(f"- Nombre de variables : {df.shape[1]}")

if "Sales" in df.columns:
    print(f"- Moyenne des ventes : {df['Sales'].mean():.2f}")
    print(f"- Ventes min/max : {df['Sales'].min()} / {df['Sales'].max()}")

if "Category" in df.columns:
    print("- Catégorie la plus rentable :",
          df.groupby('Category')["Sales"].sum().idxmax())

print("-------------------------------------------------------")

