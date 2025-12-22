# 🚀 Installation Rapide - Système de Coursier

## Installation en 3 étapes

### 1️⃣ Copier les fichiers

Créez le dossier `npc/custom/courier/` dans votre serveur rAthena et placez-y tous les fichiers :

```
npc/custom/courier/
├── config_courier.txt
├── courier_database.txt
├── courier_rewards.txt
├── courier_import.txt
├── npc_prontera.txt
├── npc_payon.txt
├── npc_geffen.txt
├── npc_alberta.txt
└── npc_morocc.txt
```

### 2️⃣ Importer les scripts

Ouvrez `conf/import/npc_scripts.conf` (ou `npc/scripts_custom.conf`)

Ajoutez cette ligne à la fin du fichier :

```
import: npc/custom/courier/courier_import.txt
```

### 3️⃣ Recharger

Redémarrez votre serveur ou utilisez :

```
@reloadscript
```

## ✅ Vérification

Le système est installé correctement si :

- Vous voyez les NPCs aux coordonnées suivantes :
  - **Prontera** (155,185) - Maître Aldric
  - **Payon** (152,75) - Maîtresse Sakura  
  - **Geffen** (120,60) - Archiviste Thaddeus
  - **Alberta** (117,56) - Capitaine Lars
  - **Morocc** (162,97) - Maître Rashid

- Aucune erreur dans le map-server au démarrage

## 🎮 Premier test

1. Allez à Prontera (155,185)
2. Parlez au Maître Aldric
3. Prenez un colis pour une autre ville
4. Voyagez vers la destination
5. Livrez le colis au Point de Livraison

## ⚙️ Configuration (Optionnel)

Pour modifier les paramètres (récompenses, rangs, etc.), éditez :

```
npc/custom/courier/config_courier.txt
```

Puis rechargez les scripts avec `@reloadscript`

## 📖 Documentation Complète

Consultez [README.md](README.md) pour :
- Détails complets du système
- Guide d'équilibrage
- Personnalisation avancée
- Dépannage

---

**C'est tout ! Votre système de coursier est prêt à l'emploi ! 🎉**
