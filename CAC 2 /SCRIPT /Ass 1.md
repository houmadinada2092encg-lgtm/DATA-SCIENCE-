<img src="image nada houmadi.jpg" style="height:264px;margin-right:264px"/>

## HOUMADI NADA

## APPOGE: 24010393
 ## Description générale de la base Iris

La base de données Iris est un jeu de données statistique emblématique, conçu à l’origine par Ronald A. Fisher en 1936. Elle est très utilisée pour l’apprentissage et la démonstration de techniques d’analyse de données et de classification automatique.


## 📊 Visualisations
Les graphiques générés sont enregistrés dans le dossier `{extract_dir}` :
- Histogrammes pour chaque variable numérique
- Matrice de corrélation (`correlation_matrix.png`)
"""

# Sauvegarde du rapport Markdown
with open("rapport_analyse.md", "w", encoding="utf-8") as f:
    f.write(md_report)

print("✅ Rapport Markdown généré : rapport_analyse.md")
print("📊 Graphiques sauvegardés dans le dossier :", extract_dir)


