1. Quel est le rôle du dossier public/ ?
C'est le seul dossier accessible depuis le navigateur. Chaque fichier y gère une page ou une action (affichage, réservation...).

2. Quel est le rôle d'une classe située dans Model ?
Elle représente un objet du domaine (salle, ligue, réservation) avec ses propriétés. Elle ne touche jamais à la base de données.

3. Quel est le rôle d'un Repository ?
Il gère les accès à la base de données il exécute le SQL et retourne les données sous forme d'objets Model.

4. Comment l'application se connecte-elle à la base de données ?
config/database.php stocke les identifiants, la classe Database (getConnection()) ouvre la connexion PDO utilisée par les repositories

5. Quel chemin est parcouru pour afficher la liste des salles ?
Navigateur → public/salles.php → SalleRepository::findAll() → Database::getConnection() → requête SQL → Base de données

6. Pourquoi utilise-t'on PDO ?
Permet d'utiliser la même syntaxe quel que soit le SGBD et sécurise l'application grâce aux requêtes préparées (anti-injection SQL)

7. Pourquoi les requêtes SQL ne sont-elle pas directement placées dans les pages PHP ?
Pour séparer la logique et l'affichage, cela évite de dupliquer le code et simplifie la maintenance si la base change

8. Quels sont les trois problèmes que tu as repérés dans l'application ?
Sécurité Mot de passe de la BDD en clair dans un fichier suivi par Git
Performance : Nouvelle connexion créée à chaque appel de getConnection()
Architecture : Logique de données et affichage HTML mélangés dans les fichiers de public/
