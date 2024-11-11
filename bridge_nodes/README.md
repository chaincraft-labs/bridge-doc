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
- Les noeuds discutent tous ensemble via le protocol `gossipsub`

### Enregistrement d'un noeud

- Les noeuds doivent être enregistrés auprès d'une authorité
  - Avec un ID unique (peer ID)
  - Avec une adresse IP
- L'authorité est un contrat sur la blockchain
- `chaincraft` à la responsabilité de maintenir cette liste de noeuds validateurs (ajout/suppression)

## 3. Fonction à implémenter

### Utilitaire

1. Générer un peer ID en fonction d'une seed

### Noeud relayer

1. Démarrer un noeud de type [rendezvous](https://en.wikipedia.org/wiki/Rendezvous_protocol)
2. Enregistrer des noeuds validateurs par peer ID
3. Génération de clés partagées pour le MPC/TSS
4. Exécuter des transactions sur la blockchain
5. Scanner les évènements depuis la blockchain

### Noeud validateur

1. Rejoindre le noeud relayer
2. Valider et signer les transactions via MPC/TSS
