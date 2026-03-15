✅ OBS Status Bars
<div align="center"> <img src="docs/preview.png" alt="OBS Status Bars Preview" width="600"> <br> <em>Real‑time monitoring for OBS · 7 metrics · Configurable thresholds · WebSocket</em> <br><br> <img src="https://img.shields.io/badge/version-1.0-blue.svg" alt="Version 1.0"> <img src="https://img.shields.io/badge/license-CC%20BY--NC%204.0-lightgrey.svg" alt="License CC BY-NC 4.0"> <img src="https://img.shields.io/badge/OBS-WebSocket%205.0+-green.svg" alt="OBS WebSocket 5.0+"> </div>
📋 Table of Contents / Sommaire
🇬🇧 English

Why?

Features

Installation

Configuration

Metrics

Technical overview

Troubleshooting

License

🇫🇷 Français

Pourquoi ?

Fonctionnalités

Installation

Configuration

Métriques

Aperçu technique

Dépannage

Licence

🇬🇧 English
🎯 Why?
When you're streaming, you need to know at a glance if everything is running smoothly:

Is the CPU struggling?

Is the encoder dropping frames?

Is the bitrate stable?

Is network congestion threatening the stream?

OBS provides these stats... but they're scattered across different panels. OBS Status Bars brings them together in a compact dock, with an intuitive visual display and fully customizable thresholds.

✨ Features
✅	Native WebSocket connection to OBS (protocol 5.0+)
✅	7 real‑time metrics: CPU, GPU, RAM, ENC, DROP, NET, CONG
✅	16‑point history → see trends at a glance
✅	Dynamic color coding (green / yellow / orange / red)
✅	Configurable thresholds for every metric
✅	Detailed tooltips on hover
✅	Auto‑reconnect with progressive backoff
✅	Optional password storage in browser
✅	Zero dependencies → single HTML file
🚀 Installation
Get the file

bash
git clone https://github.com/D-Goth/OBS-Status-Bar.git
# or just download OBS-Status-Bar.html
Open in OBS

Launch OBS Studio

Go to View → Docks → Custom Browser Docks

Enter a title (e.g. Status Bars)

Paste the full path to the HTML file
Examples:

Local: C:\Users\you\OBS-Status-Bar.html

Remote: https://your-site.com/OBS-Status-Bar.html

Click OK

The dock appears immediately. If OBS WebSocket is running without a password, the connection is automatic.

⚙️ Configuration
WebSocket setup in OBS
Tools → WebSocket Server Settings

Check Enable WebSocket server

Note the port (default: 4455)

Set a password (optional but recommended)

Connection panel
Field	Description
Host	localhost (or the OBS machine's IP)
Port	4455 (or your custom port)
Password	Leave blank if none
Remember	Stores password in browser
Adjusting thresholds
Click ⚙ Thresholds to customize the yellow and red warning levels for each metric.
Thresholds are automatically saved in your browser.

📊 Metrics
Metric	Meaning	Default thresholds	Tooltip
CPU	Processor load	⚠️ 60% · 🔴 85%	CPU : 23.5%
GPU	Render time per frame	⚠️ 60% · 🔴 85%	Render : 8.2 ms
RAM	OBS memory usage	⚠️ 60% · 🔴 85%	OBS RAM : 412 MB
ENC	Encoded vs skipped frames	⚠️ 15% · 🔴 50%	ENC skip : 2/1200
DROP	Rendered vs dropped frames	⚠️ 15% · 🔴 50%	DROP : 0/1200
NET	Actual bitrate	⚠️ 60% · 🔴 85%	Bitrate : 4850 kb/s
CONG	Network congestion	⚠️ 25% · 🔴 60%	Congestion : 12%
Note: NET and RAM percentages are relative to a dynamically adjusted maximum (auto‑scales to observed peaks).

🔧 Technical overview
Frontend: Pure HTML/CSS/JavaScript, no frameworks

Connection: WebSocket to OBS (protocol 5.0)

Authentication: Double SHA‑256 (salt + challenge)

Polling: Every 500ms via GetStats and GetStreamStatus

Storage: localStorage for thresholds and optional credentials

Key snippets:

javascript
// 16‑point circular history
const N = 16;
function push(arr, v) { arr.shift(); arr.push(Math.min(1, Math.max(0, v))); }

// Dynamic normalization (RAM / bitrate)
if (ramMB > maxRamMB * 0.8) maxRamMB = ramMB * 1.4;

// Auto‑reconnect with backoff
const RETRY_DELAYS = [5000, 5000, 10000, 10000, 30000];
❓ Troubleshooting
Issue	Solution
"Connection refused"	Check OBS is running and WebSocket is enabled
"Password required"	Either you have a password set, or OBS expects one
Bars don't move	Stream might be inactive (NET/CONG show as idle)
Dock stays empty	Verify the path to the HTML file (use absolute path)
Reconnect too slow	Delays are intentionally progressive to avoid spamming
📄 License
CC BY-NC 4.0 — Attribution - NonCommercial 4.0 International

✅ You may share and adapt the code

✅ Attribution required (credit Black‑Lab / D-Goth)

❌ No commercial use without permission

Full license

🇫🇷 Français
🎯 Pourquoi ?
Quand vous streamez, vous avez besoin de savoir en un coup d'œil si tout tient la route :

Le CPU souffre-t-il ?

L'encodage saute‑t‑il des frames ?

Le bitrate est‑il stable ?

La congestion réseau menace‑t‑elle le stream ?

OBS fournit ces stats... mais elles sont éparpillées. OBS Status Bars les regroupe dans un dock compact, avec un affichage visuel intuitif et des seuils entièrement personnalisables.

✨ Fonctionnalités
✅	Connexion WebSocket native à OBS (protocole 5.0+)
✅	7 métriques temps réel : CPU, GPU, RAM, ENC, DROP, NET, CONG
✅	Historique 16 points → visualisez les tendances
✅	Code couleur dynamique (vert / jaune / orange / rouge)
✅	Seuils configurables pour chaque métrique
✅	Tooltips détaillés au survol
✅	Reconnexion automatique avec backoff progressif
✅	Mémorisation optionnelle du mot de passe
✅	Zéro dépendance → un seul fichier HTML
🚀 Installation
Récupérez le fichier

bash
git clone https://github.com/D-Goth/OBS-Status-Bar.git
# ou téléchargez simplement OBS-Status-Bar.html
Ouvrez dans OBS

Lancez OBS Studio

Allez dans Affichage → Docks → Dock personnalisé

Donnez un titre (ex: Status Bars)

Collez le chemin complet vers le fichier HTML
Exemples :

Local : C:\Utilisateurs\vous\OBS-Status-Bar.html

Distant : https://votre-site.com/OBS-Status-Bar.html

Cliquez sur OK

Le dock apparaît immédiatement. Si OBS WebSocket est actif sans mot de passe, la connexion est automatique.

⚙️ Configuration
Activation WebSocket dans OBS
Outils → Paramètres du serveur WebSocket

Cochez Activer le serveur WebSocket

Notez le port (défaut : 4455)

Définissez un mot de passe (optionnel mais recommandé)

Panneau de connexion
Champ	Description
Hôte	localhost (ou l'IP de la machine OBS)
Port	4455 (ou votre port personnalisé)
Mot de passe	Laisser vide si aucun
Mémoriser	Stocke le mot de passe dans le navigateur
Réglage des seuils
Cliquez sur ⚙ Seuils pour personnaliser les niveaux d'alerte jaune et rouge pour chaque métrique.
Les seuils sont sauvegardés automatiquement dans votre navigateur.

📊 Métriques
Métrique	Signification	Seuils par défaut	Infobulle
CPU	Charge processeur	⚠️ 60% · 🔴 85%	CPU : 23.5%
GPU	Temps de rendu par frame	⚠️ 60% · 🔴 85%	Rendu : 8.2 ms
RAM	Mémoire utilisée par OBS	⚠️ 60% · 🔴 85%	RAM OBS : 412 MB
ENC	Frames encodées / sautées	⚠️ 15% · 🔴 50%	ENC skip : 2/1200
DROP	Frames rendues / perdues	⚠️ 15% · 🔴 50%	DROP : 0/1200
NET	Bitrate réel	⚠️ 60% · 🔴 85%	Bitrate : 4850 kb/s
CONG	Congestion réseau	⚠️ 25% · 🔴 60%	Congestion : 12%
Note : Les pourcentages pour NET et RAM sont relatifs à un maximum dynamique (auto‑ajustement selon les pics observés).

🔧 Aperçu technique
Frontend : HTML/CSS/JavaScript pur, aucun framework

Connexion : WebSocket vers OBS (protocole 5.0)

Authentification : Double SHA‑256 (salt + challenge)

Interrogation : Toutes les 500 ms via GetStats et GetStreamStatus

Stockage : localStorage pour les seuils et identifiants (optionnel)

Extraits clés :

javascript
// Historique circulaire 16 points
const N = 16;
function push(arr, v) { arr.shift(); arr.push(Math.min(1, Math.max(0, v))); }

// Normalisation dynamique (RAM / bitrate)
if (ramMB > maxRamMB * 0.8) maxRamMB = ramMB * 1.4;

// Reconnexion automatique avec backoff
const RETRY_DELAYS = [5000, 5000, 10000, 10000, 30000];
❓ Dépannage
Problème	Solution
"Connexion refusée"	Vérifiez qu'OBS est lancé et que WebSocket est activé
"Mot de passe requis"	Soit vous avez un mot de passe, soit OBS en attend un
Les barres ne bougent pas	Le stream est peut-être inactif (NET/CONG affichent inactif)
Le dock reste vide	Vérifiez le chemin du fichier HTML (chemin absolu recommandé)
Reconnexion trop lente	Les délais sont volontairement progressifs
📄 Licence
CC BY-NC 4.0 — Attribution - Pas d'Utilisation Commerciale 4.0 International

✅ Vous pouvez partager et modifier le code

✅ Attribution obligatoire (citez Black‑Lab / D-Goth)

❌ Pas d'utilisation commerciale sans autorisation

Voir la licence complète

👤 Credits / Crédits
Author / Auteur : D-Goth / Black‑Lab.fr

Inspiration : OBS native status bar... but better

Thanks : The OBS community for the excellent WebSocket protocol

📦 Releases
Version	Date	Changes
1.0	2026-03-15	Initial release · 16‑pt history · Configurable thresholds · Auto‑reconnect
<div align="center"> <b>Happy streaming! / Bon stream !</b> 🔴🎮 <br><br> <sub>Made with ❤️ in the <a href="https://black-lab.fr">Black‑Lab</a></sub> </div>
