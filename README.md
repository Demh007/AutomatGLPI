# AutomatGLPI
Automatisation de création de Tickets sur serveur GLPI par un Agent Vocal IA 




Rounded → GLPI Ticketing Automation
Automatisation complète de la prise en charge des appels entrants par un agent vocal Rounded et de la création de tickets dans GLPI via n8n, sans écrire une ligne de code métier.
🚀 Présentation

Lorsqu’un utilisateur appelle votre service via l’agent vocal Rounded, ce workflow :

    Récupère en temps réel les informations de l’appelant (nom, service, description du problème, degré d’urgence, email/téléphone).

    Initie une session sécurisée auprès de l’API REST de GLPI (initSession) en envoyant les en‑têtes App‑Token et Authorization: user_token.

    Crée un ticket GLPI (endpoint POST /Ticket) incluant toutes les données collectées.

    Termine la session GLPI (killSession) pour libérer les ressources.

    Retourne une confirmation détaillée (“Ticket #1234 créé avec succès”) à Rounded, qui la transmet immédiatement à l’appelant.

⭐ Fonctionnalités clés

    Zero‑code métier : orchestration 100 % visuelle dans n8n.

    Sécurité renforcée : tokens et URL configurés via variables d’environnement, jamais hard‑codés.

    Gestion des erreurs : si initSession ou création de ticket échoue, le workflow renvoie un message clair à l’appelant.

    Extensible : possibilité d’ajouter des champs GLPI (impact, priorités, entités), d’intégrer d’autres outils (Slack, Teams, e‑mail).

    Déploiement simplifié : compatible Docker / standalone, exposé en local via ngrok ou déployé derrière un reverse‑proxy.

🏗️ Architecture technique

Rounded (Web call)
     ↓ HTTP POST
[Webhook Rounded] ──▶ [Set Data (tokens, URL)] ──▶ [Init GLPI Session]
                                                   ↓<img width="1008" height="619" alt="image" src="https://github.com/user-attachments/assets/dcca3a1e-44dc-412f-b072-2129856c6db1" />

                                        [Create GLPI Ticket]
                                                   ↓
                                        [Kill GLPI Session]
                                                   ↓
                              [Send Response to Rounded]

    Webhook Rounded : déclencheur HTTP POST

    Set Data : nœud “Set” qui alimente app_token, user_token, glpiUrl

    HTTP Request : appels initSession, Ticket, killSession

    Webhook Response : confirmation envoyée à Rounded

⚙️ Prérequis

    GLPI (version ≥ 10) avec API REST activée (Setup → General → Enable REST API).

    Client API GLPI créé (App‑Token + User‑Token).

    n8n (v1.100+) installé localement ou en cloud.

    Rounded configuré pour pointer vers l’URL publique du webhook n8n.

    (Optionnel) ngrok pour exposer n8n en local :
