# Système de Coursier / Transporteur pour rAthena

## 📦 Description

Système économique complet de transport de marchandises entre villes pour serveurs rAthena. Les joueurs peuvent devenir des transporteurs, livrer des colis entre différentes villes, contribuer à l'économie locale et faire face à des événements aléatoires pendant leurs trajets.

## ✨ Fonctionnalités

### 🏙️ Système de Villes
- **5 villes interconnectées** : Prontera, Payon, Geffen, Alberta, Morocc
- Chaque ville produit une **ressource unique** :
  - Prontera : Farine de Blé
  - Payon : Soie Précieuse
  - Geffen : Fragment de Cristal
  - Alberta : Poisson Frais
  - Morocc : Épice Exotique
- **Système de prospérité** évolutif (6 niveaux)
- **Production automatique** de colis à partir des ressources

### 👤 Progression du Joueur
- **5 rangs de transporteur** :
  1. Apprenti Coursier (0 livraisons)
  2. Coursier (10 livraisons)
  3. Transporteur (30 livraisons)
  4. Caravannier (60 livraisons)
  5. Maître Marchand (100 livraisons)
- Bonus de récompenses croissants avec le rang
- Statistiques de livraisons persistantes

### 💰 Système de Récompenses
Les récompenses dépendent de :
- **Distance parcourue** : Plus c'est loin, plus ça paie
- **Prospérité de la ville de destination** : Villes riches = meilleures récompenses
- **Rang du transporteur** : Bonus jusqu'à +50%
- Récompenses en Zeny + Expérience

### 🎲 Événements Aléatoires
Pendant le transport, des événements peuvent survenir :
- **Attaques de bandits** : Combat contre des monstres
- **Tempêtes** : Ralentissement du joueur
- **Rencontre avec un marchand** : Bonus d'items
- **Bon vent** : Accélération + soin
- **Mendiant** : Choix moral avec récompense potentielle

### 🏪 NPCs par Ville
Chaque ville dispose de 4 NPCs :
1. **Hub de Distribution** : Récupérer des colis à livrer
2. **Dépôt d'Approvisionnement** : Contribuer avec des ressources
3. **Point de Livraison** : Livrer les colis et recevoir les récompenses
4. **Boutique de Ressources** : Acheter la ressource locale

## 📥 Installation

### Étape 1 : Copier les Fichiers

Copiez tous les fichiers du système dans votre dossier de scripts rAthena :

```
npc/custom/courier/
├── config_courier.txt
├── courier_database.txt
├── courier_rewards.txt
├── npc_prontera.txt
├── npc_payon.txt
├── npc_geffen.txt
├── npc_alberta.txt
└── npc_morocc.txt
```

### Étape 2 : Importer les Scripts

Ajoutez cette ligne dans votre fichier `conf/import/npc_scripts.conf` ou `npc/scripts_custom.conf` :

```
import: npc/custom/courier/courier_import.txt
```

OU importez directement les fichiers individuellement :

```
npc: npc/custom/courier/config_courier.txt
npc: npc/custom/courier/courier_database.txt
npc: npc/custom/courier/courier_rewards.txt
npc: npc/custom/courier/npc_prontera.txt
npc: npc/custom/courier/npc_payon.txt
npc: npc/custom/courier/npc_geffen.txt
npc: npc/custom/courier/npc_alberta.txt
npc: npc/custom/courier/npc_morocc.txt
```

### Étape 3 : Recharger les Scripts

Redémarrez votre serveur ou rechargez les scripts :

```
@reloadscript
```

## 🎮 Guide d'Utilisation

### Pour les Joueurs

1. **Prendre un colis** :
   - Rendez-vous au Hub de Distribution d'une ville
   - Parlez au Maître des Coursiers
   - Choisissez une ville de destination
   - Recevez votre colis (item 7420 - Giftbox)

2. **Transporter le colis** :
   - Voyagez vers la ville de destination
   - Attention aux événements aléatoires !
   - Ne perdez pas le colis en route

3. **Livrer le colis** :
   - Trouvez le Point de Livraison de la ville destination
   - Parlez à l'Agent de Livraison
   - Recevez vos récompenses !

4. **Contribuer à l'économie** :
   - Achetez des ressources à la Boutique locale
   - Déposez-les au Dépôt d'Approvisionnement
   - Aidez votre ville à prospérer !

### Pour les Administrateurs

#### Localisation des NPCs

**Prontera** (prontera 155,185) :
- Maître Aldric : Hub de Distribution
- Gérard : Dépôt d'Approvisionnement (150,185)
- Agent Marcel : Point de Livraison (160,185)
- Boulanger Henri : Boutique (145,185)

**Payon** (payon 152,75) :
- Maîtresse Sakura : Hub de Distribution
- Kenji : Dépôt (147,75)
- Agent Hiro : Livraison (157,75)
- Tisseuse Mei : Boutique (142,75)

**Geffen** (geffen 120,60) :
- Archiviste Thaddeus : Hub de Distribution
- Apprenti Magnus : Dépôt (115,60)
- Agent Cornelius : Livraison (125,60)
- Enchanteur Elric : Boutique (110,60)

**Alberta** (alberta 117,56) :
- Capitaine Lars : Hub de Distribution
- Pêcheur Olaf : Dépôt (112,56)
- Agent Erik : Livraison (122,56)
- Poissonnier Gustav : Boutique (107,56)

**Morocc** (morocc 162,97) :
- Maître Rashid : Hub de Distribution
- Négociant Jamal : Dépôt (157,97)
- Agent Farid : Livraison (167,97)
- Épicier Karim : Boutique (152,97)

## ⚙️ Configuration

Tous les paramètres sont modifiables dans [config_courier.txt](config_courier.txt) :

### Rangs
```cpp
setarray .RankNames$[0], "Apprenti Coursier", "Coursier", "Transporteur", "Caravannier", "Maître Marchand";
setarray .RankRequirements[0], 0, 10, 30, 60, 100;
setarray .RankBonus[0], 0, 10, 20, 35, 50; // Bonus en %
```

### Ressources
```cpp
setarray .CityResources[0], 577, 7020, 7321, 544, 7053; // IDs des items
.PackageResourceCost = 5; // Ressources nécessaires par colis
.ResourcePrice = 1000; // Prix d'achat en boutique
```

### Production
```cpp
.ProductionRate = 10; // 10 ressources = 1 colis
.MaxPackages = 50; // Limite de colis par ville
.ProductionCycle = 1800; // 30 minutes (en secondes)
```

### Prospérité
```cpp
.MaxProsperityLevel = 5;
setarray .ProsperityResourceReq[0], 0, 50, 100, 200, 350, 500;
setarray .ProsperityBonus[0], 0, 15, 30, 50, 75, 100; // Bonus en %
```

### Récompenses
```cpp
.BaseReward = 5000; // Zeny de base
.DistanceBonus = 2000; // Bonus par unité de distance
.BaseExp = 1000; // EXP de base
```

### Événements
```cpp
.EventChance = 25; // 25% de chance
.EventCheckDelay = 60; // Vérification toutes les 60 secondes
setarray .EventMonsters[0], 1031, 1063, 1109; // IDs des monstres
.MonsterCount = 3; // Nombre de monstres par attaque
```

## 🗄️ Variables du Système

### Variables Serveur (Persistantes)
- `$CourierCityResources[0-4]` : Stock de ressources par ville
- `$CourierCityPackages[0-4]` : Stock de colis par ville
- `$CourierCityProsperity[0-4]` : Niveau de prospérité par ville
- `$CourierCityContributions[0-24]` : Contributions pour amélioration (5 ressources × 5 villes)

### Variables Joueur (Persistantes)
- `courier_deliveries` : Nombre total de livraisons effectuées

### Variables Temporaires (Session)
- `courier_transport_active` : Transport en cours (0/1)
- `courier_transport_source` : Ville source (0-4)
- `courier_transport_dest` : Ville destination (0-4)
- `courier_transport_time` : Timestamp de début

## 🛠️ Équilibrage

### Calcul des Récompenses

**Formule de base :**
```
Récompense = Base × (1 + RangBonus%) × (1 + ProspéritéBonus%) + (Distance × BonusDistance)
```

**Exemple concret :**
- Livraison de Prontera (0) vers Morocc (4) = Distance de 4
- Rang Caravannier (+35%)
- Prospérité niveau 3 à Morocc (+50%)
- Base = 5000 Zeny

```
5000 × 1.35 × 1.50 + (4 × 2000)
= 10125 + 8000
= 18125 Zeny
```

### Progression Recommandée

| Rang | Livraisons | Temps estimé | Récompense moyenne |
|------|------------|--------------|-------------------|
| Apprenti | 0-9 | 1-2h | 7000-9000 Zeny |
| Coursier | 10-29 | 2-4h | 9000-12000 Zeny |
| Transporteur | 30-59 | 4-8h | 12000-16000 Zeny |
| Caravannier | 60-99 | 8-15h | 16000-20000 Zeny |
| Maître Marchand | 100+ | 15h+ | 20000-25000 Zeny |

## 🐛 Dépannage

### Les colis ne sont pas générés
- Vérifiez que `CourierDatabase::OnProductionCycle` est lancé
- Assurez-vous que les villes ont des ressources (`$CourierCityResources`)
- Vérifiez `.ProductionCycle` dans la config

### Le joueur ne reçoit pas de récompenses
- Vérifiez qu'il a bien l'item 7420 (Giftbox) dans son inventaire
- Vérifiez que `courier_transport_dest` correspond à la ville actuelle
- Regardez les logs du serveur pour les erreurs

### Les événements ne se déclenchent pas
- Vérifiez `.EventChance` dans la config (25 = 25%)
- Assurez-vous que le timer `OnEventCheck` est actif
- Les monstres dans `.EventMonsters` doivent exister dans votre DB

### Erreur "undefined variable"
- Vérifiez que `config_courier.txt` est chargé EN PREMIER
- Relancez `@reloadscript` après modification

## 📊 Monitoring

### Commandes GM Utiles

Créez des commandes personnalisées pour monitorer le système :

```cpp
// Vérifier le stock d'une ville
@script dispbottom "Prontera - Ressources: " + $CourierCityResources[0] + " | Colis: " + $CourierCityPackages[0];

// Vérifier la prospérité
@script dispbottom "Prospérité Prontera: " + $CourierCityProsperity[0];

// Reset des statistiques d'un joueur
@script courier_deliveries = 0;

// Ajouter des ressources à une ville
@script $CourierCityResources[0] += 100;
```

## 🎨 Personnalisation

### Ajouter de Nouvelles Villes

1. Modifiez `config_courier.txt` :
   - Ajoutez les noms dans `.CityNames$`
   - Ajoutez les coordonnées dans `.CityCoords`
   - Ajoutez les maps dans `.CityMaps$`
   - Ajoutez l'ID de ressource dans `.CityResources`

2. Créez un nouveau fichier `npc_nomville.txt` basé sur les existants

3. Ajoutez l'import dans `courier_import.txt`

### Modifier les Événements

Éditez `courier_rewards.txt`, fonction `TriggerRandomEvent` :
- Ajoutez de nouveaux types d'événements
- Modifiez les probabilités avec `rand()`
- Créez des sous-fonctions pour les nouveaux événements

### Changer les Récompenses

Éditez `courier_rewards.txt`, fonction `CalculateReward` :
- Modifiez les formules de calcul
- Ajoutez des bonus spéciaux
- Intégrez d'autres facteurs (temps, météo, etc.)

## 📝 Compatibilité

- **Version rAthena** : Dernière version stable (testée sur 2023+)
- **Syntaxe** : rAthena native (pas Hercules)
- **Base de données** : Compatible SQL et TXT
- **Encodage** : UTF-8 (pour les accents français)

## 🆘 Support

### Problèmes Connus

1. **Encoding des accents** : Si les accents ne s'affichent pas correctement, vérifiez que vos fichiers sont en UTF-8
2. **Item 7420** : Assurez-vous que Giftbox (7420) existe dans votre item_db
3. **Timers multiples** : Si plusieurs joueurs sont en transport, les timers peuvent se chevaucher (comportement normal)

### Logs à Vérifier

```
map-server.log : Erreurs de script
sql-server.log : Problèmes de variables SQL
```

## 🤝 Contributions

Ce système est fourni "tel quel" et peut être modifié librement pour votre serveur.

## 📜 License

Libre d'utilisation et de modification pour tout serveur rAthena.

## 🎯 Crédits

Système créé spécifiquement pour Sunrise Harbor Server.
Développement basé sur les spécifications du document "General Idea".

---

**Bon jeu et bonnes livraisons ! 🚚📦**
