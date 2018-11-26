
# PROSIT ALLER

  

## Mots Clés

-   Intégrité référentielle * : Situation dans laquelle pour chaque information d'une table A qui fait référence à une information d'une table B, ,l'information dans la table B existe. C'est donc une cohérence de la BDD. On peut donc mettre des contraintes, pour marquer la dépendance et empêcher de supprimer l'information B.
    
-   ADO.net * : Set de classes qui permettent d’interagir avec des sources de données (SQL Server / XML...) dans le framework .NET
    
-   Modèle relationnel
    
-   Dans les règles de l’art
    
-   Selon le cahier des charges
    
-   Réutilisable 

(*à définir)

## Contexte


Quoi ?

-   Présenter une architecture fonctionnelle sur les commerciaux et leurs téléphones
    
-   Utiliser une BDD
    
-   Créer un logiciel pour une société
    
-   Résoudre pb code
    

Comment ?

-   En utilisant ADO.NET
    
-   Utiliser BDD
    

Pourquoi ?

-   Pour gérer les commerciaux des lignes téléphoniques (historique)
    
-   Réutiliser le code (modulaire)
    

  

## Contraintes

Nothin’

## Problématique

-   Comment interagir avec une base de données sur .NET ?
    
-   Comment rendre réutilisable son code dans un environnement .NET ?
    
-   Comment rendre générique l’accès aux données ?


## Généralisation

-   Gestion
    
-   Liaison de données
    
-   Architecture

## Hypothèses

-   Utilisation CAD permet l’abstraction.
    
-   ADO permet de faire le lien entre programme et BDD.
    
-   ADO.NET ➔ ORM

## Plan d’Action

Etudier :

-   ADO.NET
    
-   Application en couche
    

Réalisation :

-   WS

## ADO.NET

### Architecture
- Set de classes qui permettent d’interagir avec des sources de données (SQL Server / XML...) dans le framework .NET; mais également aux sources de données qui passent par OLE DataBase.

- Extension d'ADO
- Architecture d'accès aux données (orienté "architecture réseau")
- Décomposé en deux Composants:
	- **Fournisseur managé :** Toutes les classes pouvant communiquer avec la source de données.
	- **Dataset :** Toutes les classes liées au jeu d'enregistrement.
![](https://www.tutorialspoint.com/asp.net/images/ado.net_objects.jpg)

**Dataset** :

![](https://www.javatpoint.com/ado/images/ado-net-introduction1.png)
- BDD Relationnelle **locale** à l'application 
- Copie conforme ou tronquée d'une base existante
- Une reconnexion est nécessaire pour la mettre à jour
- Contient DataTable : Représentant la table (BDD / Tables & relations)

DataSet est préférable à DataReader pour les cas suivants: 
- Cache local dans l'application, on peut donc le manipuler. 
	- Si on a juste besoin de lire des résultats de query ⇒ **DataReader**.
- Les données distantes proviennent d'un XML Web service
- On peut manipuler les données dynamiquement (lié à des forms...)
- Meilleures performances sans connexion à la source de données, qui libère la connexion pour d'autres users.


**Data Providers / Fournisseur managé :**

- Utilisé pour connecter la database, exécuter les commandes, et retrouver les enregistrements 
- 'Connection' est un objet pour permettre la connectivité. Ouvrir une connexion.
- 'Command' permet de retourner des données, modifier des données, lancer des procédures, envoyer / retrouver des informations mis en paramètre. Gestion des paramètres.
- 'DataReader' fournit de bonnes performances de diffusion de données à partir de la source . (vu avant)
- 'DataAdapter' fournit un pont entre le '**DataSet**' ( et la source de données, et utilise 'Command' pour mettre à jour entre le DataSet et la source. Regroupe les fonctionnalités de la commande de création et des modifications vers la source. Permet d'avoir un environnement de développement cohérent et performant.

### EF6 - ORM - **ADO.NET Entity Framework** : 
 ⇒ C'est une ORM éprouvé pour .NET
 ⇒ Version 6 (EF6)

## Application en couche :

Architecture trois couches :
- **Présentation :** affichage, restitution sur le poste de travail, dialogue avec l'utilisateur.
- **Traitement :** mise en œuvre de l'ensemble des règles de gestion et de la logique applicative.
- **Accès aux données :**  Données qui sont destinées à être conservées sur la durée / définitive.

Les trois couches communiquent entre elles, via un modèle d'échange, chacun apportant un service rendu.

![](https://upload.wikimedia.org/wikipedia/commons/1/18/3tier-fr.png)

Le but répond à des objectifs :
- Allégement du poste de travail client 
- Hétérogénéité des plateformes (serveurs / clients / Langages...)
- Introduction aux clients dis "légers" (technologies intranet / HTML)
- Amélioration de la sécurité des données, pas de liens clients et donnes. Le serveur s'occupe de vérifier l'intégrité et la validité des données avant de les envoyer à la CAD.
- Rupture entre application et données. On sépare les deux, la BDD peut-être plus facilement normalisée et intégrée.
- Meilleure répartition de la charge entre différents serveurs d'applications


## Vidéos du prosit :

**Commandes pour créer les objets nécessaire à ADO.NET : 
```C#
	private string rq_sql; //requête
        private string cnx; //connexion
        private System.Data.OleDb.OleDbConnection oCNX; //Objet Connexion pour se connecter
        private System.Data.OleDb.OleDbCommand oCMD; //Objet Commande pour exécuter les requêtes SQL
        private System.Data.OleDb.OleDbDataAdapter oDA; //Objet Adapter fera le lien entre l'appli et la BDD
        private System.Data.DataSet oDS; //Recevra / stocker en local les informations de la BDD
```
