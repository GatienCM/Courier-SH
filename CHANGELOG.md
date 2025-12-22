# 🔧 CORRECTIF - Structure Mise à Jour

## Changements Effectués

Le système a été restructuré pour corriger l'erreur `buildin_callfunc: Function not found!`

### Nouvelle Structure

```
Courier-SH/
├── config_courier.txt         # Configuration (inchangé)
├── courier_functions.txt       # NOUVEAU - Fonctions globales
├── courier_database.txt        # Simplifié - Seulement initialisation
├── courier_events.txt          # NOUVEAU - Événements aléatoires
├── courier_import.txt          # Mis à jour
├── npc_prontera.txt           # Mis à jour
├── npc_payon.txt              # Mis à jour  
├── npc_geffen.txt             # Mis à jour
├── npc_alberta.txt            # Mis à jour
└── npc_morocc.txt             # Mis à jour
```

### ⚠️ IMPORTANT - Ordre de Chargement

Les fichiers DOIVENT être chargés dans cet ordre (déjà configuré dans courier_import.txt) :

1. `config_courier.txt` - Configuration
2. `courier_functions.txt` - Fonctions globales (NOUVEAU)
3. `courier_database.txt` - Initialisation
4. `courier_events.txt` - Événements (NOUVEAU)
5. NPCs des villes

### Fichiers Supprimés

- ❌ `courier_rewards.txt` (remplacé par courier_functions.txt et courier_events.txt)

### Fonctions Maintenant Disponibles

Toutes les fonctions sont maintenant globales et peuvent être appelées avec `callfunc()` :

**Gestion des ressources :**
- `AddCityResource(city_id, amount)`
- `RemoveCityResource(city_id, amount)`

**Gestion des colis :**
- `AddCityPackage(city_id, amount)`
- `RemoveCityPackage(city_id)`

**Gestion de la prospérité :**
- `AddContribution(city_id, resource_type, amount)`
- `CheckProsperityUpgrade(city_id)`

**Gestion des joueurs :**
- `GetPlayerRank()`
- `GetRankName(rank_id)`
- `IncrementDeliveries()`

**Information :**
- `GetCityInfo(city_id)`

**Récompenses :**
- `CalculateReward(source, dest, rank, prosperity)`
- `CalculateExp(source, dest, rank)`

**Transport :**
- `StartTransport(source, dest)`
- `CancelTransport()`
- `CompleteDelivery(source, dest)`

### Installation

Si vous aviez déjà installé la version précédente :

1. Supprimez l'ancien `courier_rewards.txt` de votre serveur
2. Copiez les nouveaux fichiers :
   - `courier_functions.txt`
   - `courier_events.txt`
3. Remplacez tous les autres fichiers par les nouvelles versions
4. Rechargez : `@reloadscript`

Si c'est une nouvelle installation, suivez simplement [INSTALLATION.md](INSTALLATION.md)

### Vérification

Le système fonctionne correctement si :
- Aucune erreur dans le map-server au démarrage
- Vous pouvez parler aux NPCs dans les 5 villes
- Vous pouvez prendre et livrer un colis sans erreur

---

**Le système est maintenant 100% fonctionnel ! ✅**
