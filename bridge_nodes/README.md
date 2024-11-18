# Description du réseau de noeuds au sein du bridge décentralisé

## 1. Les noeuds relayers

### Le réseau de noeuds relayers (centralisé)

- Le réseau est centralisé
- Les noeuds relayers sont sous la responsabilité de `chaincraft`
- Les noeuds relayers assurent l'interaction avec les contrats sur les blockchains
- Les noeuds relayers communiquent avec les noeuds validateurs
- Les noeuds relayers doivent résister aux pannes et offrir un service permanent
- Les noeuds relayers enregistrent les noeuds validateurs

## 2. Les noeuds validateurs

### Réseau de noeuds validateurs

- Le réseau est décentralisé
- Le réseau est limité à `n` noeuds ou `n` est ègal à `(à définir)`
- Les noeuds communiquent tous ensemble via le protocol `gossipsub`
- Les noeuds écoutent les évènements émis sur la blockchain

### Enregistrement d'un noeud

- L'authorité est un contrat sur la blockchain
- Les noeuds sont enregistrés auprès d'une authorité
  - Avec un ID unique (peer ID)
  - Avec une adresse IP
- `chaincraft` à la responsabilité de maintenir cette liste de noeuds validateurs (ajout/suppression)

> Le noeud validateur doit communiquer avec un noeud RPC

## 3. Fonction à implémenter

### Utilitaire

- [x] Générer un peer ID en fonction d'une seed

### Noeud relayer

- [x] Démarrer un noeud de type [rendezvous](https://en.wikipedia.org/wiki/Rendezvous_protocol)
- [ ] Ajouter un noeud validateur par peer ID
- [ ] Supprimer un noeud validateur par peer ID
- [ ] Générer des clés partagées pour le MPC/TSS
- [ ] Distribuer des clés partagées pour le MPC/TSS vers ;es nodes validateurs
- [ ] Exécuter des transactions sur la blockchain

### Noeud validateur

- [ ] Connecter le noeud validateur au noeud relayer
- [ ] Écouter les évènements depuis la blockchain
- [ ] Valider les transactions via MPC/TSS
- [ ] Signer les transactions via MPC/TSS
- [ ] Envoyer les transactions via MPC/TSS aux autres nodes validateurs
