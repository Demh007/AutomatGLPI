
<br><img width="861" height="428" alt="workflow" src="https://github.com/user-attachments/assets/ad684380-fce4-4d29-854a-8a3194f5ec77" />
<br>
AutomatGLPI est un protoype de workflow n8n qui fait le lien entre l’agent vocal IA Rounded et l’API REST de GLPI pour créer automatiquement des tickets.
<br>
Pourquoi je l’ai créé ?
Durant mon stage, j’ai constaté que les techniciens étaient fréquemment dérangés par des appels pour des problèmes qu’ils renvoyaient invariablement vers GLPI : “Il faut créer un ticket.” Cette double manipulation (répondre au téléphone, puis saisir le ticket) engendrait :
   - Des temps de latence dans le traitement des demandes.
   - Des oublis ou des tickets incomplets.
   - Une frustration des utilisateurs et des techniciens.
<br>     
<br>
J’ai donc conçu ce workflow n8n + Rounded + GLPI pour automatiser à la volée la création de tickets, libérer du temps aux équipes et garantir une meilleure réactivité.

    Étape 1 : Rounded reçois un appel sur un numéro et envoie à n8n un webhook contenant les infos de l’appelant (nom, service, description, urgence, contact).

    Étape 2 : Un nœud Set prépare les variables (app_token, user_token, glpiUrl).

    Étape 3 : n8n appelle GET /initSession sur GLPI pour obtenir un session_token.

    Étape 4 : n8n poste un nouveau ticket (POST /Ticket) avec les données de l’appel et le session_token.

Ce process 100 % low‑code supprime la saisie manuelle des tickets, réduit les délais de prise en charge et assure une traçabilité immédiate dans GLPI.
<br>
<br>
<img width="1100" height="489" alt="wehbook" src="https://github.com/user-attachments/assets/ae0bc4a9-ebfa-463f-aa99-f621a2971d2a" />
<img width="1175" height="882" alt="ticket1" src="https://github.com/user-attachments/assets/557cb492-a58e-4f21-828e-a26d9c9be12d" />
<br>
<br>


