# Scrapping et stockage des données dans une base vectorielle Qdrant 

Ce projet est un outil de scraping web avec génération d'embeddings NLP, stockage dans Qdrant Cloud et recherche sémantique. Il permet de :

- Scraper le contenu détaillé d’un cours en ligne avec BeautifulSoup
- Télécharger automatiquement les ressources associées (PDF, images, vidéos)
- Générer des embeddings NLP avec Sentence-Transformers
- Stocker ces vecteurs dans Qdrant Cloud
- Réaliser une recherche sémantique à partir d’une question en langage naturel

## Installation 
1. Cloner le dépot
```
git clone https://github.com/Famdia/scraping-to-qdrant-semantic-search.git
```
Ce projet est fourni sous forme de notebook Colab. L’installation des dépendances est déjà prévue dans la première cellule. Pour une première exécution, il suffit de décommenter la ligne correspondante, puis de la remettre en commentaire afin d’éviter de réinstaller les bibliothèques à chaque lancement.

```
!pip install beautifulsoup4 requests sentence-transformers qdrant-client
```
## Configuration de Qdrant Cloud
Nous utilisons Qdrant Cloud comme solution d’hébergement de la base vectorielle. Cela permet d’éviter une configuration locale et de garantir un 
accès distant et sécurisé à la base de données.
Donc, pour que le projet puisse s'exécuter correcter, il faut :
- Créez un compte gratuit sur Qdrant Cloud
- Créez une instance vectorielle
- Copiez l’URL et la clé API
- Remplacez les valeurs vides dans le code python :
```
client = QdrantClient(
    url="",  # mettez ici l'URL Qdrant Cloud
    api_key=""  # mettez ici votre clé API
)
```
## Exemple de recherche sémantique
- Question :
```
Comment prévenir les risques techniques dans la construction ?
```
- Sortie :
```
--- Résultats de la recherche ---
Score : 0.6044
Titre : Bâtiment : risques techniques et naturels, comprendre et agir
Texte : Comprendre les enjeux (techniques, climatiques...) et mieux connaître les grands principes dans le domaine de la construction Être alerté sur les principaux risques (techniques, naturels, organisationnels, parfois juridiques, pathologiques futures...) Connaître les moyens de prévention et en particulier avoir les recommandations sur la conception et la mise en oeuvre, découvrir des bonnes pratiques transversales (compétences, organisation, interfaces...), être sensibilisés à l'entretien/maintenance etc.
Lien : https://www.mooc-batiment-durable.fr/fr/formations/mooc-batiment-risques-techniques-naturels-comprendre-et-agir/
```
