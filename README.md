# 🎮 NIRD Quest - Jeu Éducatif sur le Numérique Responsable

Un jeu RPG éducatif en ligne développé dans le cadre de la Nuit de l'Info 2025. Le joueur explore un village médiéval-fantastique et interagit avec des PNJ pour répondre à des quiz sur le Numérique Inclusif, Responsable et Durable (NIRD).

---

## 📋 Fonctionnalités Réalisées

### 🎮 Gameplay
- **Exploration libre** : Déplacez-vous dans un village pixelisé avec les touches directionnelles ou le D-Pad tactile
- **Système de quêtes** : 9 quêtes éducatives avec des PNJ uniques
- **Quiz interactifs** : Questions à choix multiples sur le numérique responsable
- **Système de points** : Gagnez des points en répondant correctement aux questions
- **Progression sauvegardée** : Votre avancement est conservé localement

### 👥 Multijoueur
- **Temps réel** : Voyez les autres joueurs se déplacer en direct via WebSocket
- **Synchronisation des équipes** : Scores partagés entre membres d'une même équipe
- **Système de kick** : Un seul joueur par équipe peut être connecté simultanément

### 🎨 Interface
- **Page d'accueil immersive** : Présentation du projet NIRD avec animations
- **Mini-quiz** : Testez vos connaissances avant de jouer
- **Design pixel-art** : Style rétro inspiré des jeux Zelda classiques
- **Responsive** : Jouable sur mobile avec D-Pad tactile

### 🔐 Authentification
- **Connexion utilisateur** : Système de login avec email/mot de passe
- **Gestion des équipes** : Chaque joueur appartient à une équipe
- **Persistance** : Token JWT stocké localement

### 🏆 Système de Scores
- **Classement des équipes** : Tableau des scores en temps réel
- **Points par quête** : Différentes valeurs selon la difficulté
- **Synchronisation serveur** : Scores persistés en base de données

---

## 🛠️ Stack Technique

### Frontend (`main-project-front/`)
- **React 19** avec TypeScript
- **Vite** pour le bundling
- **Tailwind CSS** pour le styling
- **Framer Motion** pour les animations
- **Socket.io-client** pour le temps réel
- **React Router** pour la navigation

### Backend (`main-project-back/`)
- **Node.js** avec Express
- **Socket.io** pour WebSocket
- **Prisma ORM** avec PostgreSQL
- **TypeScript**

---

## 🚀 Installation et Lancement

### Prérequis
- **Node.js** v20 ou supérieur
- **npm** ou **yarn**
- **PostgreSQL** (pour le backend)

### 1. Cloner le projet
```bash
git clone https://github.com/moetezbouazra/nuit-info-2025-main-challenge.git
cd nuit-info-2025-main-challenge
```

### 2. Configuration du Backend

```bash
cd main-project-back

# Installer les dépendances
npm install

# Configurer les variables d'environnement
cp .env.example .env  # ou créer un fichier .env

# Contenu du fichier .env :
# DATABASE_URL="postgresql://user:password@localhost:5432/nird_game"
# PORT=3009
# CORS_ORIGIN="http://localhost:5173"

# Générer le client Prisma
npx prisma generate

# Appliquer les migrations (si la base existe)
npx prisma db push

# Lancer le serveur de développement
npm run dev
```

Le serveur backend sera accessible sur `http://localhost:3009`

### 3. Configuration du Frontend

```bash
cd main-project-front

# Installer les dépendances
npm install

# Configurer les variables d'environnement (optionnel)
# Créer un fichier .env.local avec :
# VITE_API_URL=http://localhost:3001/api
# VITE_WS_URL=http://localhost:3009

# Lancer le serveur de développement
npm run dev
```

Le frontend sera accessible sur `http://localhost:5173`

### 4. Accéder au jeu
1. Ouvrez votre navigateur sur `http://localhost:5173`
2. Parcourez la page d'accueil pour découvrir le projet NIRD
3. Cliquez sur "Commencer l'aventure"
4. Connectez-vous avec vos identifiants
5. Explorez le village et parlez aux PNJ !

---

## 🐳 Lancement avec Docker

### Backend
```bash
cd main-project-back
docker build -t nird-backend .
docker run -p 3009:3009 -e DATABASE_URL="..." nird-backend
```

### Frontend
```bash
cd main-project-front
docker build -t nird-frontend \
  --build-arg VITE_API_URL=http://localhost:3001/api \
  --build-arg VITE_WS_URL=http://localhost:3009 \
  .
docker run -p 80:80 nird-frontend
```

---

## 🎯 Commandes Utiles

### Frontend
| Commande | Description |
|----------|-------------|
| `npm run dev` | Lance le serveur de développement |
| `npm run build` | Compile le projet pour la production |
| `npm run preview` | Prévisualise le build de production |
| `npm run lint` | Vérifie le code avec ESLint |

### Backend
| Commande | Description |
|----------|-------------|
| `npm run dev` | Lance le serveur avec hot-reload |
| `npm run build` | Compile TypeScript |
| `npm run start` | Lance le serveur compilé |
| `npx prisma studio` | Ouvre l'interface Prisma |

---

## 📁 Structure du Projet

```
nuit-info-2025-main-challenge/
├── main-project-front/          # Application React
│   ├── src/
│   │   ├── components/game/     # Composants du jeu
│   │   ├── pages/               # Pages de l'application
│   │   ├── hooks/               # Hooks React personnalisés
│   │   ├── data/                # Données des quêtes
│   │   └── services/            # API et services
│   └── public/                  # Assets statiques
│
├── main-project-back/           # Serveur Node.js
│   ├── src/
│   │   ├── server.ts            # Point d'entrée
│   │   ├── playerManager.ts     # Gestion des joueurs
│   │   └── types.ts             # Types TypeScript
│   └── prisma/
│       └── schema.prisma        # Schéma de base de données
│
└── README.md                    # Ce fichier
```

---

## 🎓 Thème Éducatif

Le jeu sensibilise aux enjeux du **Numérique Inclusif, Responsable et Durable (NIRD)** :

- 🔒 Souveraineté des données et RGPD
- 🐧 Logiciels libres (Linux, LibreOffice)
- ♻️ Reconditionnement du matériel informatique
- 🌱 Éco-conception numérique
- 🔐 Cybersécurité et bonnes pratiques
- 🌍 Accessibilité numérique

---

## 👥 Équipe

Projet réalisé dans le cadre de la **Nuit de l'Info 2025**.

---

## 📄 Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.
