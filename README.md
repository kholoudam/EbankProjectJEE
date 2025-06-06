<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Projet eBank - Documentation</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        h1, h2 {
            color: #2c3e50;
            border-bottom: 2px solid #3498db;
            padding-bottom: 10px;
        }
        .image-container {
            margin: 20px 0;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            background-color: #f9f9f9;
        }
        .image-container img {
            max-width: 100%;
            height: auto;
            display: block;
            margin: 10px auto;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .description {
            background-color: #e8f4fc;
            padding: 15px;
            border-radius: 5px;
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <h1>Backend Spring Boot</h1>
    
    <div class="image-container">
        <img src="pics/ebank6.png" alt="Interface H2 Database - Requête vide">
        <div class="description">
            <strong>ebank6.png - Requête SQL vide</strong><br>
            Interface H2 Database avec une requête qui ne retourne aucun résultat.<br>
            - Connexion à la base H2 en mémoire: jdbc:h2:mem:bank<br>
            - Structure visible: tables ACCOUNT_OPERATION, BANK_ACCOUNT, CUSTOMER<br>
            - La requête SELECT * FROM CUSTOMER ne retourne aucune ligne
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank7.png" alt="Interface H2 Database - Requête avec résultats">
        <div class="description">
            <strong>ebank7.png - Requête SQL avec résultats</strong><br>
            Interface H2 Database avec une requête qui retourne des clients.<br>
            - Même base H2 que ebank6<br>
            - La requête SELECT * FROM CUSTOMER retourne 3 clients:<br>
            &nbsp;&nbsp;• Hassan (Hassan@gmail.com)<br>
            &nbsp;&nbsp;• Yassine (Yassine@gmail.com)<br>
            &nbsp;&nbsp;• Aicha (Aicha@gmail.com)<br>
            - Incohérence avec les autres captures (probablement des sessions/test différents)
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank8.png" alt="Table ACCOUNT_OPERATION">
        <div class="description">
            <strong>ebank8.png - Opérations bancaires</strong><br>
            Capture de la table ACCOUNT_OPERATION dans la base H2.<br>
            - Affiche 18 opérations bancaires avec montants, dates, types (CREDIT/DEBIT) et IDs de comptes<br>
            - Deux comptes bancaires distincts identifiés par des UUID<br>
            - Montants avec une précision décimale élevée<br>
            - Toutes les opérations datées du 04/05/2025 avec des timestamps précis
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank1.png" alt="Création d'un client - ibrahim">
        <div class="description">
            <strong>ebank1.png - Création d'un client</strong><br>
            Capture montrant une requête POST pour créer un nouveau client via l'API REST.<br>
            - Endpoint: http://localhost:8085/customers<br>
            - Méthode: POST<br>
            - Corps: JSON avec name="ibrahim" et email="ibrahim@gamil.com"<br>
            - Réponse: Succès (200 OK) avec l'objet client créé (id=11)<br>
            - Temps de réponse: 9 ms
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank2.png" alt="Liste des clients - format incorrect">
        <div class="description">
            <strong>ebank2.png - Liste des clients (format incorrect)</strong><br>
            Capture montrant une requête GET pour récupérer la liste des clients, mais avec un format JSON malformé.<br>
            - Endpoint: http://localhost:8085/customers<br>
            - Méthode: GET<br>
            - Problème: Réponse JSON contient des erreurs de syntaxe (accolades et virgules mal placées)<br>
            - On voit quand même plusieurs clients avec leurs id, name et email
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank3.png" alt="Liste des clients - affichage navigateur">
        <div class="description">
            <strong>ebank3.png - Liste des clients (affichage navigateur)</strong><br>
            Affichage dans un navigateur de la liste des clients.<br>
            - Même endpoint que ebank2 mais affiché différemment<br>
            - Liste de 8 clients avec leurs id, name et email<br>
            - La présence de "..." suggère qu'il y a plus de clients non affichés
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank4.png" alt="Création d'un client - malak">
        <div class="description">
            <strong>ebank4.png - Création d'un autre client</strong><br>
            Une autre requête POST pour créer un client.<br>
            - Création d'un client avec name="malak" et email="malak@gamil.com"<br>
            - Réponse avec id=15 (suggère que la base contient au moins 15 clients)<br>
            - Note: Faute de frappe dans l'email ("gamil.com" au lieu de "gmail.com")
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank5.png" alt="Suite de la liste des clients">
        <div class="description">
            <strong>ebank5.png - Suite de la liste des clients</strong><br>
            Suite de la liste des clients montrée dans ebank3.<br>
            - Affiche les clients avec id de 8 à 15<br>
            - Confirme que le client "ibrahim" (id=11) a bien été créé<br>
            - Le client "malak" (id=15) correspond à celui créé dans ebank4
        </div>
    </div>

    <h2>Frontend Angular</h2>

    <div class="image-container">
        <img src="pics/ebank10.png" alt="Interface de recherche clients">
        <div class="description">
            <strong>ebank10.png - Interface de recherche clients</strong><br>
            Interface simplifiée de recherche de clients.<br>
            - Barre de recherche par mot-clé<br>
            - Affichage tabulaire des clients (ID, Name, Email)<br>
            - Liste réduite de 3 clients (Hassan, Imane, Mohamed)
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank11.png" alt="Liste des clients (frontend)">
        <div class="description">
            <strong>ebank11.png - Liste des clients (frontend)</strong><br>
            Interface Angular (localhost:4200) affichant la liste des clients.<br>
            - Affiche les clients avec IDs 7 à 19<br>
            - Boutons "OK/Annuler" suggèrent une fonctionnalité de confirmation<br>
            - Menu avec options "Dashboard" et "MyFib" (peut-être d'autres modules)
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank12.png" alt="Recherche de client">
        <div class="description">
            <strong>ebank12.png - Recherche de client</strong><br>
            Résultats de recherche pour le mot-clé "image".<br>
            - Retourne 5 clients nommés "Image" avec le même email<br>
            - Suggère une fonctionnalité de recherche/filtre opérationnelle
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank13.png" alt="Création de client réussie">
        <div class="description">
            <strong>ebank13.png - Création de client réussie</strong><br>
            Message de confirmation après création d'un client.<br>
            - Message: "Customer has been successfully saved!"<br>
            - Formulaire pour un nouveau client "lala" (lala@gmail.com)<br>
            - Bouton "Save" pour valider
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank14.png" alt="Liste des derniers clients">
        <div class="description">
            <strong>ebank14.png - Liste des derniers clients</strong><br>
            Affichage partiel d'une liste de clients.<br>
            - Affiche les clients 18 (Imane), 19 (Mohamed) et 21 (lala)<br>
            - Mention "Accounts" répétée pour chaque client (probablement un bouton/lien)
        </div>
    </div>

    <div class="image-container">
        <img src="pics/ebank15.png" alt="Détails d'un compte bancaire">
        <div class="description">
            <strong>ebank15.png - Détails d'un compte bancaire</strong><br>
            Interface de gestion d'un compte spécifique.<br>
            - Compte ID: 1c68c33d-7a76-4519-9d7c-f8cb72fc56d4<br>
            - Solde affiché: 1,417,246.80 (format monétaire)<br>
            - Liste des 5 dernières opérations avec montants importants<br>
            - Formulaire pour nouvelle opération (DEBIT/CREDIT/TRANSFER)
        </div>
    </div>
</body>
</html>