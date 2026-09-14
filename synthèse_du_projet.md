## 📋 SYNTHÈSE COMPLÈTE DU PROJET CLARA-IA
--- 
**🎯 SYNTHÈSE DU PROJET**
**📌 Présentation Générale**
**Clara-IA** est un **assistant vocal intelligent** développé en **Node.js** qui fonctionne **entièrement en local** sur Windows. C'est un projet évolutif qui a commencé comme un projet scolaire (S.A.R.A.H) et est devenu un assistant personnel complet.

Élément	                Valeur

Nom	                   Clara-IA (anciennement JarvisIA, S.A.R.A.H, Mathilde)
Version	                V1.0
Langage	                Node.js (JavaScript)
Plateforme	             Windows
Architecture	          Modulaire (plugins)
Nombre de plugins	       35+
Créateur	                Frédéric Hermann (P'tit Fred)
Début du projet	       2013 (S.A.R.A.H)
Refonte actuelle	       2026

**🏗️ ARCHITECTURE TECHNIQUE**
```text
┌────────────────────────────────────────────────────────┐
│                    CLARA-IA                            │
├────────────────────────────────────────────────────────┤
│                                                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │   Node.js    │  │   Chrome     │  │   Windows    │  │
│  │   (Serveur)  │  │  (Interface) │  │  (Système)   │  │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  │
│         │                 │                 │          │
│         └─────────────────┼─────────────────┘          │
│                           │                            │
│  ┌────────────────────────▼────────────────────────┐   │
│  │           COMMUNICATION SSE (HTTPS)             │   │
│  │              Port 4300                          │   │
│  └────────────────────────┬────────────────────────┘   │
│                           │                            │
│  ┌────────────────────────▼────────────────────────┐   │
│  │              35 PLUGINS ACTIFS                  │   │
│  │  Reconnaissance | Info | Courses | Mémoire ...  │   │
│  └─────────────────────────────────────────────────┘   │
│                                                        │
└────────────────────────────────────────────────────────┘
```
**📁 STRUCTURE DES FICHIERS**

```text
C:\ClaraIA\
│
├── 📂 script/                          # Code serveur
│   ├── 📄 wsrnode.js                  # Serveur principal
│   ├── 📄 function.js                 # Fonctions globales
│   ├── 📄 traitement.js               # Traitement des requêtes
│   ├── 📄 plugin.js                   # Gestion des plugins
│   ├── 📄 start.js                    # Démarrage automatique
│   ├── 📄 research-ia.js              # Recherche IA (Gemini)
│   ├── 📄 webcam-service.js           # Service webcam
│   ├── 📄 webcam-control.js           # Contrôle webcam
│   ├── 📄 cleanup.js                  # Nettoyage
│   │
│   ├── 📂 bin/
│   │   ├── 📄 ffmpeg.exe              # Capture webcam
│   │   └── 📄 nircmd.exe              # Commandes Windows
│   │
│   └── 📂 static/                     # Frontend
│       ├── 📄 index.html              # Page principale
│       ├── 📂 css/
│       │   └── 📄 style.css
│       └── 📂 js/
│           ├── 📄 events.js           # SSE + voix
│           ├── 📄 mainhtml.js         # Reconnaissance vocale
│           ├── 📄 voices.js
│           ├── 📄 meteo.js
│           └── 📄 ...
│
├── 📂 plugins/                         # 35+ plugins
│   ├── 📂 bonjour/                    # Reconnaissance faciale + salutation
│   ├── 📂 face_recognition/           # Reconnaissance faciale
│   ├── 📂 info/                       # Actualités RSS
│   ├── 📂 courtoisie/                 # Scénario quotidien
│   ├── 📂 courses/                    # Liste de courses
│   ├── 📂 memoire/                    # Base de données personnes
│   ├── 📂 meteo/                      # Météo
│   ├── 📂 programme/                  # Gestion logiciels
│   ├── 📂 suntzu/                     # Citations Sun Tzu
│   ├── 📂 journal_de_bord/            # Journal de bord
│   └── 📂 ...                         # + 25 autres
│
├── 📂 temp/                            # Fichiers temporaires
├── 📂 logs/                            # Logs
└── 📄 journal.json                     # Journal de bord
```

✅ FONCTIONNALITÉS PRINCIPALES
🎤 1. Reconnaissance Vocale
Technologie : Web Speech API (Chrome)

Langue : Français

Déclencheur : "Clara" + commande

Exemple : "Clara bonjour"

🔊 2. Synthèse Vocale (TTS)
Technologie : Web Speech API

Voix : Chrome (locale)

Personnalisation : Randomisation des réponses

📷 3. Reconnaissance Faciale
Technologie : Jimp (comparaison pixel)

Base de données : plugins/face_recognition/database/faces/

Seuil : 65% de différence

Optimisation : Cache des photos, résolution 160x120

🧠 4. Plugin Mémoire
Stockage : Fichiers JSON individuels

Informations : Nom, prénom, âge, relations, signe zodiaque

Relations : Familiales (père, mère, frère...) et sociales (ami, collègue...)

📰 5. Actualités
Source : Google News RSS

Rafraîchissement : Toutes les 15 minutes

Affichage : Zone INFOMODIALE

📅 6. Scénario Quotidien
Source : Fichiers JSON (semaine/mois/anniversaires)

Rafraîchissement : Toutes les 5 minutes

Affichage : Zone SCENARIO

📋 7. Liste de Courses
Stockage : coursesmemoire.json

Actions : Ajout, suppression, vidage, envoi SMS

🌤️ 8. Météo
Source : Orange Météo / OpenWeatherMap

Commandes : "Clara météo [ville]"

📚 9. Citations Sun Tzu
Base : 212 citations (L'Art de la Guerre)

Thèmes : Planification, Stratégie, Adaptation, Commandement

💻 10. Gestion des Logiciels
Scan : C:\Program Files, C:\Program Files (x86), AppData\Local\Programs

Action : Lancement/fermeture de logiciels

Sécurité : Blocage des navigateurs

💪 POINTS FORTS DU PROJET
✅ Architecture
Modulaire : 35+ plugins indépendants

Extensible : Ajout facile de nouveaux plugins

Auto-détection : Webcam, IP, chemins

Cross-plugin : Communication entre plugins

✅ Interface
Moderne : Design Jarvis avec animations

Temps réel : SSE (Server-Sent Events)

Défilant : Marquee pour SCENARIO et INFOMODIALE

Responsive : Adaptation à l'écran

✅ Intelligence
IA Gemini : Recherche intelligente

Reconnaissance faciale : Identification visuelle

Mémoire persistante : Souvenirs des personnes

Analyse de sentiment : Détection d'humeur

✅ Robustesse
Fallbacks : Méthodes alternatives

Gestion d'erreurs : Try/catch partout

Cache : Optimisation des performances

Nettoyage : Fichiers temporaires gérés

✅ Sécurité
HTTPS : Certificats auto-signés

Blocklist : Navigateurs interdits

Isolation : Chaque plugin séparé

Validation : Vérification des entrées

📊 STATISTIQUES
Métrique	Valeur
Lignes de code	~15 000
Fichiers JS	50+
Plugins actifs	10
Plugins passifs	25
Temps de démarrage	~3 secondes
Temps de reconnaissance	~1 seconde
Mémoire utilisée	~100 MB
Ports utilisés	4300 (HTTPS), 8091 (musique)
🔧 TECHNOLOGIES UTILISÉES
Catégorie	Technologie	Utilisation
Backend	Node.js	Serveur principal
Framework	Express	Serveur HTTP
Communication	SSE (sse-emitter)	Temps réel
Images	Jimp	Manipulation photos
Webcam	FFmpeg	Capture vidéo
IA	Google Gemini	Recherche intelligente
RSS	rss-parser	Actualités
Dates	Moment.js	Gestion temporelle
Matching	Levenshtein	Correspondance floue
Frontend	Chrome	Reconnaissance vocale
Système	Nircmd	Commandes Windows
🎯 COMMANDES DISPONIBLES
text
🎤 RECONNAISSANCE
   Clara bonjour              → Reconnaissance faciale + salutation
   Clara reconnais            → Identification visuelle
   Clara qui est ce           → Identification visuelle

📰 ACTUALITÉS
   Clara info                 → Actualités Google News
   Clara actualités           → Actualités Google News

🌤️ MÉTÉO
   Clara météo Paris          → Météo de Paris
   Clara météo Lyon           → Météo de Lyon

📋 COURSES
   Clara ajoute du lait       → Ajoute à la liste
   Clara enlève du lait       → Retire de la liste
   Clara liste des courses    → Affiche la liste
   Clara efface la liste      → Vide la liste

🧠 MÉMOIRE
   Clara ajoute Thomas        → Ajoute une personne
   Clara qui est Thomas ?     → Informations sur Thomas
   Clara tu connais Thomas ?  → Vérifie si connu
   Clara arbre de Thomas      → Arbre familial
   Clara anniversaire         → Anniversaires à venir
   Clara liste des personnes  → Liste toutes les personnes

📚 CITATIONS
   Clara citation Sun Tzu     → Citation aléatoire
   Clara citation Sun Tzu stratégie     → Citation sur la stratégie
   Clara citation Sun Tzu planification → Citation sur la planification

💻 LOGICIELS
   Clara lance Firefox        → Lance Firefox
   Clara ferme Firefox        → Ferme Firefox

📅 DATE/HEURE
   Clara heure                → Heure actuelle
   Clara date                 → Date actuelle
   Clara jour                 → Jour de la semaine

📓 JOURNAL
   Clara journal              → Lit le journal de bord
   Clara ajoute au journal [texte] → Ajoute une entrée
🚀 AMÉLIORATIONS FUTURES
Court terme
□ Ajouter plus de voix (Google Cloud TTS)
□ Améliorer la reconnaissance faciale (face-api.js)
□ Mode veille avec activation vocale
□ Interface mobile responsive
Moyen terme
□ Intégration Spotify/Netflix
□ Plugin rappels (agenda)
□ Reconnaissance des émotions
□ Multi-utilisateurs
Long terme
□ Apprentissage automatique
□ Objets connectés (IoT)
□ Version web/mobile
□ API publique
