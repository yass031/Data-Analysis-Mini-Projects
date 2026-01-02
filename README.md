# 🎓 DataCamp Analysis Projects Portfolio

Collection de projets d'analyse de données réalisés sur DataCamp, démontrant des compétences pratiques en nettoyage, exploration et visualisation de données avec l'écosystème Python de data science.

## 📊 Aperçu des Projets

### 🏫 1. Exploration des Résultats aux Tests des Écoles Publiques de NYC
**Objectif** : Analyser les performances au SAT des écoles publiques de New York pour identifier les meilleures institutions et examiner les modèles au niveau des arrondissements.  
**Compétences démontrées** :
- Filtrage et agrégation de données avec Pandas
- Analyse statistique (moyenne, écart-type)
- Classement et comparaison des performances scolaires
- Manipulation et nettoyage de données CSV

**Fichiers** :
- `notebook.ipynb` - Notebook Jupyter avec l'analyse complète
- `schools.csv` - Données des résultats aux tests des écoles NYC
- `schoolbus.jpg` - Image de présentation du projet

**Code principal** :
```python
# Écoles avec les meilleurs résultats en maths
best_math_schools = schools[schools["average_math"] >= 640][["school_name", "average_math"]]

# Top 10 des écoles par score SAT total
schools["total_SAT"] = schools["average_math"] + schools["average_reading"] + schools["average_writing"]
top_10_schools = schools[["school_name", "total_SAT"]].sort_values("total_SAT", ascending=False).head(10)

# Arrondissement avec la plus grande variabilité de scores
boroughs = schools.groupby("borough")["total_SAT"].agg(["count", "mean", "std"]).round(2)