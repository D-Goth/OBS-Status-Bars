# **OBS Status Bars**

Real‑time monitoring for OBS · 7 metrics · Configurable thresholds · WebSocket

![Vue globale avec le chat Twitch](https://github.com/D-Goth/OBS-Status-Bar/raw/main/status_bar_twitch.png)
![Panneau de configuration OBS Status Bars](https://github.com/D-Goth/OBS-Status-Bar/raw/main/Config_Panel.png)
![Barre de statut OBS Status Bars](https://github.com/D-Goth/OBS-Status-Bar/raw/main/Status_Bar.png)

**Version** : 1.0  
**Licence** : CC BY‑NC 4.0  
**Auteur** : D‑Goth / Black‑Lab  
**Compatibilité** : OBS WebSocket 5.0+

---

## 📋 Table of Contents / Sommaire

- [🇬🇧 English](#-english)
  - [Why?](#why)
  - [Features](#features)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Metrics](#metrics)
  - [Technical overview](#technical-overview)
  - [Troubleshooting](#troubleshooting)
  - [License](#license)
- [🇫🇷 Français](#-français)
  - [Pourquoi ?](#pourquoi)
  - [Fonctionnalités](#fonctionnalités)
  - [Installation](#installation-1)
  - [Configuration](#configuration-1)
  - [Métriques](#métriques)
  - [Aperçu technique](#aperçu-technique)
  - [Dépannage](#dépannage)
  - [Licence](#licence-1)

---

## 🇬🇧 English

### 🎯 Why?

When you're streaming, you need to know instantly whether everything is running smoothly:

- Is the CPU struggling?
- Is the encoder skipping frames?
- Is the bitrate stable?
- Is network congestion threatening the stream?

OBS provides these stats, but they are scattered across multiple panels.  
**OBS Status Bars** brings them together in a compact dock with intuitive visual feedback and customizable thresholds.

### ✨ Features

- ✅ Native WebSocket connection to OBS (protocol 5.0+)
- ✅ 7 real‑time metrics: CPU, GPU, RAM, ENC, DROP, NET, CONG
- ✅ 16‑point history for trend visualization
- ✅ Dynamic color coding (green / yellow / orange / red)
- ✅ Configurable thresholds per metric
- ✅ Detailed tooltips on hover
- ✅ Auto‑reconnect with progressive backoff
- ✅ Optional password storage
- ✅ Zero dependencies — single HTML file

### 🚀 Installation

**Get the file**

```bash
git clone https://github.com/D-Goth/OBS-Status-Bar.git
# or download OBS-Status-Bar.html
```

**Add to OBS**

1. Open **OBS Studio**
2. Go to **View → Docks → Custom Browser Docks**
3. Enter a title (e.g. `Status Bars`)
4. Paste the **full path** to the HTML file  
   *Example:* `C:\Users\you\OBS-Status-Bar.html`
5. Click **OK**

If OBS WebSocket is active **without a password**, the connection is automatic.

### ⚙️ Configuration

**WebSocket setup in OBS**

- **Tools → WebSocket Server Settings**
  - Enable WebSocket server
  - Note the port (default: **4455**)
  - Set a password (optional)

**Connection panel**

| Field      | Description                     |
|------------|---------------------------------|
| **Host**   | `localhost` or OBS machine IP   |
| **Port**   | 4455 (or custom)                |
| **Password** | Leave blank if none           |
| **Remember** | Stores password in browser    |

**Thresholds**

Click **⚙ Thresholds** to adjust yellow/red warning levels.  
Settings are saved automatically.

### 📊 Metrics

| Metric | Meaning                    | Default thresholds | Tooltip example       |
|--------|----------------------------|--------------------|------------------------|
| **CPU**  | Processor load             | 60% / 85%          | `CPU : 23.5%`          |
| **GPU**  | Render time                | 60% / 85%          | `Render : 8.2 ms`      |
| **RAM**  | OBS memory usage           | 60% / 85%          | `OBS RAM : 412 MB`     |
| **ENC**  | Encoded vs skipped frames  | 15% / 50%          | `ENC skip : 2/1200`    |
| **DROP** | Rendered vs dropped frames | 15% / 50%          | `DROP : 0/1200`        |
| **NET**  | Actual bitrate             | 60% / 85%          | `Bitrate : 4850 kb/s`  |
| **CONG** | Network congestion         | 25% / 60%          | `Congestion : 12%`     |

> **Note**: NET and RAM auto‑scale to observed peaks.

### 🔧 Technical overview

- Pure HTML/CSS/JavaScript
- WebSocket protocol 5.0
- Double SHA‑256 authentication
- Polling every 500 ms
- `localStorage` for thresholds and credentials

**Key snippets**

```javascript
// 16‑point circular history
const N = 16;
function push(arr, v) { arr.shift(); arr.push(Math.min(1, Math.max(0, v))); }
```

```javascript
// Dynamic normalization
if (ramMB > maxRamMB * 0.8) maxRamMB = ramMB * 1.4;
```

```javascript
// Auto‑reconnect with backoff
const RETRY_DELAYS = [5000, 5000, 10000, 10000, 30000];
```

### ❓ Troubleshooting

| Issue               | Solution                          |
|---------------------|-----------------------------------|
| Connection refused  | Ensure OBS WebSocket is enabled   |
| Password required   | OBS expects one                   |
| Bars not moving     | Stream may be inactive            |
| Dock empty          | Use an absolute path              |
| Reconnect slow      | Backoff is intentional            |

### 📄 License

**CC BY‑NC 4.0** — Attribution · NonCommercial

- ✅ You may share and adapt
- ✅ Attribution required
- ❌ No commercial use

[Full license](https://creativecommons.org/licenses/by-nc/4.0/)

### 👤 Credits

- **Author**: D‑Goth / [Black‑Lab.fr](https://black-lab.fr)
- **Inspiration**: OBS native status bar
- **Thanks**: OBS community

---

## 🇫🇷 Français

### 🎯 Pourquoi ?

Quand vous streamez, vous devez savoir immédiatement si tout tient la route :

- Le CPU souffre‑t‑il ?
- L’encodage saute‑t‑il des frames ?
- Le bitrate est‑il stable ?
- La congestion réseau menace‑t‑elle le stream ?

OBS fournit ces informations, mais elles sont dispersées.  
**OBS Status Bars** les regroupe dans un dock compact, clair et configurable.

### ✨ Fonctionnalités

- ✅ Connexion WebSocket native (5.0+)
- ✅ 7 métriques en temps réel
- ✅ Historique 16 points
- ✅ Code couleur dynamique
- ✅ Seuils configurables
- ✅ Tooltips détaillés
- ✅ Reconnexion automatique
- ✅ Mémorisation optionnelle du mot de passe
- ✅ Un seul fichier HTML

### 🚀 Installation

```bash
git clone https://github.com/D-Goth/OBS-Status-Bar.git
# ou téléchargez OBS-Status-Bar.html
```

Puis dans OBS :

1. **Affichage → Docks → Dock personnalisé**
2. Donnez un titre
3. Collez le **chemin complet** vers le fichier HTML
4. Validez

### ⚙️ Configuration

**Activer WebSocket dans OBS**

- **Outils → Paramètres du serveur WebSocket**
  - Activer
  - Noter le port
  - Définir un mot de passe (optionnel)

**Panneau de connexion**

| Champ         | Description                     |
|---------------|---------------------------------|
| **Hôte**      | `localhost` ou IP OBS           |
| **Port**      | 4455                            |
| **Mot de passe** | Laisser vide si aucun         |
| **Mémoriser** | Stocke le mot de passe          |

**Seuils**

Cliquez **⚙ Seuils** pour ajuster les niveaux jaune/rouge.

### 📊 Métriques

*(Identique à la version anglaise)*

| Métrique | Signification                 | Seuils par défaut | Exemple d'infobulle |
|----------|-------------------------------|-------------------|---------------------|
| **CPU**  | Charge processeur             | 60% / 85%         | `CPU : 23.5%`       |
| **GPU**  | Temps de rendu                | 60% / 85%         | `Rendu : 8.2 ms`    |
| **RAM**  | Mémoire utilisée par OBS      | 60% / 85%         | `RAM OBS : 412 MB`  |
| **ENC**  | Frames encodées / sautées     | 15% / 50%         | `ENC skip : 2/1200` |
| **DROP** | Frames rendues / perdues      | 15% / 50%         | `DROP : 0/1200`     |
| **NET**  | Bitrate réel                  | 60% / 85%         | `Bitrate : 4850 kb/s` |
| **CONG** | Congestion réseau             | 25% / 60%         | `Congestion : 12%`  |

### 🔧 Aperçu technique

*(Identique à la version anglaise)*

- HTML/CSS/JavaScript pur
- Protocole WebSocket 5.0
- Authentification double SHA‑256
- Interrogation toutes les 500 ms
- `localStorage` pour seuils et identifiants

### ❓ Dépannage

| Problème              | Solution                         |
|-----------------------|----------------------------------|
| Connexion refusée     | Vérifier que WebSocket est activé |
| Mot de passe requis   | OBS en attend un                 |
| Barres immobiles      | Stream peut être inactif         |
| Dock vide             | Utiliser un chemin absolu        |
| Reconnexion lente     | Backoff intentionnel             |

### 📄 Licence

**CC BY‑NC 4.0** — Attribution · Pas d’usage commercial

### 👤 Crédits

- **Auteur** : D‑Goth / [Black‑Lab.fr](https://black-lab.fr)
- **Inspiration** : barre d’état OBS
- **Merci** : communauté OBS

---

<div align="center">
  <b>Bon stream !</b> 🔴🎮<br>
  <sub>Made with ❤️ in the Black‑Lab</sub>
</div>

---
