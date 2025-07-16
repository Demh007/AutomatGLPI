# AutomatGLPI
Automatisation de création de Tickets sur serveur GLPI par un Agent Vocal IA 




    Réception de l’appel sur l'Agent Rounded 

        Rounded envoie un webhook HTTP POST à n8n avec les infos de l’appel (nom, service, description, urgence, contact).
        <img width="1021" height="812" alt="rounded" src="https://github.com/user-attachments/assets/1fe9d2a8-a4c0-4808-9d2b-66fae9cd6d49" />


        


    Préparation des données

        Nœud Set (« configuration_glpi ») :

            Stocke app_token, user_token et l’URL de l’API GLPI (glpiUrl).

            <img width="1886" height="567" alt="image" src="https://github.com/user-attachments/assets/04c228d2-8cd7-450f-ad89-fcacc3212054" />

            


    Ouverture de session GLPI

        Nœud HTTP Request (« Init GLPI Session ») → GET {{glpiUrl}}/initSession

        En‑têtes :

            App-Token: {{app_token}}

            Authorization: user_token {{user_token}}

        Récupère et stocke le session_token.
         <img width="1374" height="785" alt="image" src="https://github.com/user-attachments/assets/13d7feb5-d1ca-41cb-a10e-6190345a7724" />


        

    Création du ticket

        Nœud HTTP Request (« Create GLPI Ticket ») → POST {{glpiUrl}}/Ticket

        Body JSON : titre, description, urgence, nom de l’appelant, etc.

        En‑têtes : mêmes + Session-Token: {{session_token}}.
<img width="267" height="884" alt="image" src="https://github.com/user-attachments/assets/5caf29be-1ba6-47d8-93d5-dd0eb44c8b4d" />
<img width="263" height="476" alt="image" src="https://github.com/user-attachments/assets/1f82b902-d168-4c20-9c3f-cde750f82428" />

  

    Retour d’information à Rounded

        Nœud Respond to Webhook :

            Envoie à Rounded le résumé du ticket créé (numéro, statut, lien…).

GLPI reçois le ticket 
<img width="1298" height="886" alt="image" src="https://github.com/user-attachments/assets/1a4072a5-85ff-4177-ac82-080365807d5a" />
            


