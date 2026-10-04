# 🇪🇸 Mis abuelos, mis padres y yo — jeu d'espagnol

Ce dossier contient une version web du jeu, avec :
- pseudo ;
- 20 questions mélangées ;
- vocabulaire + questions sur le tableau ;
- questions « ¿Cómo se dice...? » ;
- questions à 1, 2 ou 3 réponses correctes ;
- 2 types de questions écrites avec 25 secondes ;
- 15 secondes pour les QCM ;
- 3 vies ;
- classement partagé via Supabase.

## Barème

### Question avec 1 réponse correcte
- 1 bonne : 100 points
- 0 bonne : 0 point

### Question avec 2 réponses correctes
- 2 bonnes : 100 points
- 1 bonne : 50 points
- 0 bonne : 0 point

### Question avec 3 réponses correctes
- 3 bonnes : 100 points
- 2 bonnes : 50 points
- 1 bonne : 25 points
- 0 bonne : 0 point

Aucun bonus de rapidité ne modifie ces points.

## Obtenir un vrai lien + classement partagé

Le plus simple est d'utiliser **Supabase + GitHub Pages**.

### 1. Créer la base de données
1. Crée un projet sur Supabase.
2. Ouvre le SQL Editor.
3. Copie-colle tout le contenu de `supabase.sql`.
4. Exécute-le.
5. Dans Project Settings > API, récupère :
   - Project URL
   - Publishable/anon key

### 2. Connecter le jeu
Ouvre `index.html` et trouve :

const SUPABASE_URL="";
const SUPABASE_ANON_KEY="";

Mets tes valeurs entre les guillemets.

Exemple :
const SUPABASE_URL="https://xxxxx.supabase.co";
const SUPABASE_ANON_KEY="ta-cle-publique";

Ne mets JAMAIS une clé secrète/service_role dans le fichier.

### 3. Obtenir le lien du jeu
Méthode simple avec GitHub Pages :
1. Crée un dépôt GitHub, par exemple `jeu-espagnol`.
2. Mets `index.html` dans le dépôt.
3. Va dans Settings > Pages.
4. Choisis Deploy from branch.
5. Sélectionne la branche `main` et le dossier `/root`.
6. GitHub donnera une adresse du type :
   https://TON-PSEUDO.github.io/jeu-espagnol/

Cette adresse pourra être envoyée aux autres joueurs.

### Important pour le classement
Le classement est réellement partagé entre les joueurs une fois Supabase configuré : les scores sont enregistrés dans la table `scores`.

Pour un classement scolaire réellement fiable, il faudrait ajouter une protection anti-triche côté serveur, car un site statique ne peut pas empêcher quelqu'un de modifier son score dans son navigateur.
