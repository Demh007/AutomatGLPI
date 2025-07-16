
# AutomatGLPI
Automatisation de création de Tickets sur serveur GLPI par un Agent Vocal IA

1/ Réception de l’appel sur l'Agent Rounded  
Rounded envoie un webhook HTTP POST à n8n avec les infos de l’appel (nom, service, description, urgence, contact).

<img width="443" height="715" alt="image" src="https://github.com/user-attachments/assets/9dee964a-5b3a-4b5a-a530-d7c6a2e9ab90" />
<br />
<br />
<br />
2/ Préparation des données  
Nœud Set (« configuration_glpi ») :  
stocke app_token, user_token et l’URL de l’API GLPI (glpiUrl).

<img width="265" height="688" alt="20" src="https://github.com/user-attachments/assets/7dcd1837-1b29-49e5-9607-55d7c7a281fe" />
<br />
<br />
<br />
3/ Ouverture de session GLPI  
<img width="273" height="855" alt="image" src="https://github.com/user-attachments/assets/f1f0b00c-7368-48ff-a23f-c99eab16b6e9" />
<br />
<br />
<br />
4/ Création du ticket  
<img width="267" height="884" alt="image" src="https://github.com/user-attachments/assets/5caf29be-1ba6-47d8-93d5-dd0eb44c8b4d" /><img width="263" height="476" alt="image" src="https://github.com/user-attachments/assets/1f82b902-d168-4c20-9c3f-cde750f82428" />  
<br />
<br />
<br />
5/ GLPI reçoit bien le ticket  

<img width="1298" height="886" alt="image" src="https://github.com/user-attachments/assets/1a4072a5-85ff-4177-ac82-080365807d5a" />
<br />
<br />
<br />
Pour accéder au workflow complet, obtenir une démo privée ou discuter d’une licence d’exploitation contactez :
mehdiazzimani.pro@gmail.com
            


