# Le Back

### ebank6.png - Requête SQL vide

![Requête vide](pics/ebank6.png)

Description : Interface H2 Database avec une requête qui ne retourne aucun résultat  
- Connexion à la base H2 en mémoire: `jdbc:h2:mem:bank`  
- Structure visible: tables `ACCOUNT_OPERATION`, `BANK_ACCOUNT`, `CUSTOMER`  
- La requête `SELECT * FROM CUSTOMER` ne retourne aucune ligne

---

### ebank7.png - Requête SQL avec résultats

![Requête avec résultats](pics/ebank7.png)

Description : Requête SQL affichant 3 clients  
- Même base H2 que ebank6  
- Clients : Hassan, Yassine, Aicha  
- Incohérence avec les autres captures → sessions différentes ?

---

### ebank8.png - Opérations bancaires

![Opérations bancaires](pics/ebank8.png)

Description : Table `ACCOUNT_OPERATION` avec 18 opérations  
- Montants, dates, types (CREDIT/DEBIT), comptes UUID  
- Toutes datées du 04/05/2025 avec timestamps précis

---

### ebank1.png - Création d'un client

![Création client](pics/ebank1.png)

Description : Requête POST pour créer un client via l'API REST  
- Endpoint: `http://localhost:8085/customers`  
- Méthode: POST  
- Données : name="ibrahim", email="ibrahim@gamil.com"  
- Réponse : 200 OK, client créé avec `id=11`, Temps : 9 ms

---

### ebank2.png - Liste des clients (format incorrect)

![Liste incorrecte](pics/ebank2.png)

Description : GET `/customers` retourne un JSON malformé  
- Problème de syntaxe (accolades/virgules)  
- Affiche tout de même les clients avec leurs infos

---

### ebank3.png - Liste des clients (navigateur)

![Liste navigateur](pics/ebank3.png)

Description : Affichage HTML de `/customers`  
- 8 clients listés avec leurs ID, nom, email  
- Présence de "..." → d'autres clients cachés

---

### ebank4.png - Création d’un autre client

![Autre création](pics/ebank4.png)

Description : POST `/customers` avec  
- name="malak", email="malak@gamil.com"  
- Réponse : `id=15`  
- ⚠️ Typo : "gamil.com" au lieu de "gmail.com"

---

### ebank5.png - Suite de la liste des clients

![Suite liste](pics/ebank5.png)

Description : Clients affichés de id=8 à id=15  
- Confirme que "ibrahim" et "malak" ont été créés

---

# Le Front

### ebank10.png - Interface de recherche clients

![Recherche clients](pics/ebank10.png)

Description :  
- Barre de recherche  
- Tableau des clients (ID, Name, Email)  
- 3 clients : Hassan, Imane, Mohamed

---

### ebank11.png - Liste des clients (frontend)

![Liste Angular](pics/ebank11.png)

Description : Interface Angular `localhost:4200`  
- Clients de ID 7 à 19  
- Boutons de confirmation (OK/Annuler)  
- Menu : Dashboard, MyFib, etc.

---

### ebank12.png - Recherche de client

![Recherche "image"](pics/ebank12.png)

Description :  
- Recherche du mot-clé "image"  
- 5 clients "Image" affichés → filtre fonctionnel

---

### ebank13.png - Création de client réussie

![Client sauvegardé](pics/ebank13.png)

Description :  
- Message : "Customer has been successfully saved!"  
- Client "lala" (lala@gmail.com)  
- Bouton "Save"

---

### ebank14.png - Liste des derniers clients

![Derniers clients](pics/ebank14.png)

Description :  
- Clients : 18 (Imane), 19 (Mohamed), 21 (lala)  
- Bouton/lien "Accounts" présent

---

### ebank15.png - Détails d'un compte bancaire

![Détails compte](pics/ebank15.png)

Description :  
- Compte ID : `1c68c33d-7a76-4519-9d7c-f8cb72fc56d4`  
- Solde : 1,417,246.80  
- 5 dernières opérations listées  
- Formulaire pour nouvelle opération

---

## 🧠 Synthèse technique

Le projet complet comprend :

### ✅ Backend Spring Boot
- API REST pour la gestion des clients (CRUD)
- Gestion des comptes bancaires et opérations
- Base H2 en mémoire avec schéma relationnel

### ✅ Frontend Angular
- Interface sur `localhost:4200`
- Fonctionnalités : liste, recherche, création de clients
- Visualisation des comptes et opérations
- Exécution d'opérations bancaires

### 🧱 Modèle de données
- **Clients** : ID, nom, email  
- **Comptes** : ID (UUID), solde  
- **Opérations** : montant, type, date, compte_id

### 🔄 Flux complet
Créer un client → lui associer un compte → effectuer des opérations → consulter l’historique

---