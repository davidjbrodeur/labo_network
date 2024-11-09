# Laboratoire 7 - Analyser un réseau

**Objectifs** : Ce laboratoire pratique est conçu pour vous permettre d’observer le fonctionnement des réseaux en temps réel, d’interagir avec les différentes couches de communication, et d'utiliser des outils pour comprendre et analyser votre réseau. Vous allez explorer les commandes et outils pour détecter et protéger les réseaux. 

**Prérequis** : Assurez-vous d’avoir un ordinateur sous Ubuntu et d’avoir installé les outils suivants :
- **EtherApe** : pour la visualisation du trafic réseau en temps réel
- **Nmap** : pour analyser les réseaux et détecter les appareils connectés ainsi que les ports ouverts

**Instructions** :

---

## Partie 1 : Visualisation du trafic réseau (/5)

1. **Lancez EtherApe** :
   - Ouvrez un terminal.
   - Entrez la commande suivante pour démarrer EtherApe avec les droits administratifs :
     ```bash
     sudo etherape
     ```
   - **Mot de passe** : entrez votre mot de passe administrateur (ou celui du compte).

2. **Ouvrez un navigateur web** :
   - Placez la fenêtre d’EtherApe sur une moitié de votre écran.
   - Sur l’autre moitié, ouvrez Firefox et accédez au site suivant : `http://ubuntu.com`.

3. **Observation du frafic** :
   - Dans EtherApe, observez en temps réel le trafic généré par la connexion à `ubuntu.com`.
   - Lancez le téléchargement de la distribution Ubuntu pour générer plus de trafic.

4. **Analysez le trafic** :
   - Cliquez sur la zone rouge dans EtherApe pour afficher plus de détails.
   - **Questions** :  
     - Pourquoi ce site envoie-t-il autant de paquets ?
     - Quelle est la nature des paquets envoyés et comment est-ce qu'ils sont représentés ?
   
5. **Annulation** :
   - Annulez le téléchargement et fermez Firefox.

## Partie 2 : Exploration du réseau (/5)

1. **Trouver l’adresse IP de votre station** :
   - Dans un nouvel onglet terminal, entrez la commande suivante pour afficher les interfaces réseau :
     ```bash
     ip a
     ```
   - **Note** : Identifiez et notez l’adresse IP de votre station (indice : éliminez les autres interfaces pour trouver celle qui correspond à votre connexion actuelle).

2. **Analyse de réseau local avec Nmap** :
   - Lancez la commande suivante en remplaçant `VotreIP` par votre adresse IP, en ajoutant `/24` pour balayer l’ensemble du réseau :
     ```bash
     nmap -sn VotreIP/24
     ```
   - **Questions** :
     - Quelle est l’adresse IP du réseau que vous venez de scanner ?
     - Parmi les appareils trouvés, quelles adresses IP appartiennent à d’autres appareils sur le réseau ?

3. **Analyse des ports** :
   - Utilisez Nmap pour découvrir les ports ouverts sur un appareil spécifique (remplacez `IPcible` par l’adresse IP de l’appareil que vous ciblez) :
     ```bash
     nmap -Pn -T4 IPcible
     ```
   - **Explication** : L’option `-T4` indique la vitesse du scan, où -T2 est lent et -T5 est rapide mais moins fiable.
   - **Question** : Quels ports ouverts sont visibles sur cet appareil ?

4. **Expérimentation de filtrage** (facultatif, 1 point bonus) :
   - Si vous avez activé un pare-feu (comme UFW sur Ubuntu), testez un scan Nmap avant et après son activation pour voir l’effet.
   - **Questions** :
     - Quel effet a eu l’activation du pare-feu sur les résultats de votre scan ?
     - Quelle différence avez-vous observée dans EtherApe suite à l’activation ?

---

## Partie 3 : Réflexion et exploration (/5)

1. **Compréhension des Outils** :
   - Dans vos mots, à quoi sert Nmap ? 
   - Quel est l’intérêt d’utiliser EtherApe dans l’analyse réseau ?
   - Quel est le rôle d’un pare-feu dans la protection des réseaux ?

2. **Exploration Supplémentaire** (facultatif, 1 point bonus) :
   - **Traceroute** : Utilisez la commande `traceroute` pour identifier le chemin pris par vos données jusqu’à `ubuntu.com` :
     ```bash
     traceroute ubuntu.com
     ```
   - **Ping** : Effectuez un test de latence vers `ubuntu.com` avec la commande `ping` pour observer les temps de réponse :
     ```bash
     ping -c 5 ubuntu.com
     ```
   - **Analyse de Paquets** (Avancé) : Installez et lancez Wireshark pour observer les paquets détaillés (besoin d’autorisation administrative).
   - **Réflexion** : Explorer les éléments précédents. Donnez une explication du fonctionnement des outils et comment ils peuvent être utile dans une attaque et/ou pour analyser en défence. 

---

**Feedback** : Après avoir terminé ce laboratoire, n'hésitez pas à partager vos remarques constructives pour améliorer les futures versions.
