# ` 🦺 `︲Doc-Technique-Installation-Windows-11

---

## ` 📑 `︲Sommaire

1. [` 🛠️ `︲Préparation de l'environnement](#preparation-de-lenvironnement)
   - [` 💿 `︲Installation de Windows 11 (client)](#installation-de-windows)
   - [` 💿 `︲Installation de Windows Server 2025 (serveur)](#installation-de-windows-server)

2. [` 🏛️ `︲Installation et configuration du contrôleur de domaine](#installation-et-configuration-du-controleur-de-domaine)
   - [` 🔧 `︲Installation des rôles AD DS et DNS](#installation-roles-ad-ds-et-dns)
   - [` 🌐 `︲Promotion du serveur et création du domaine descartesbleu.org](#promotion-du-serveur-et-creation-du-domaine)

3. [` ✅ `︲Conclusion et Annexes](#conclusion)
4. [`🧰`︲Outils et Ressources utilisés pour la création de cette documentation.](#outils-et-ressources)

---

<a id="introduction"></a>
## `📘`︲Introduction

---

<a id="contexte-et-objectifs-du-tp"></a>
> [!NOTE]
> Tu vas apprendre à configurer un domaine, comprendre le rôle d’un contrôleur de domaine, gérer efficacement les utilisateurs et les groupes, appliquer des stratégies de groupe (GPO) et automatiser certaines tâches courantes grâce à PowerShell. > L’objectif est de te permettre de mettre en place un environnement réseau fonctionnel et de maîtriser les bases essentielles de l’administration système dans un contexte professionnel.

---

<a id="presentation-de-larchitecture-reseau-et-des-outils-utilises"></a>
> [!IMPORTANT]
> **Présentation des outils et prérequis :**
> - `🖥️`︲**Client :** Windows 11
> - `🔧`︲**Outils :** VMware
> - ` 📦 `︲**VMWare :** ︲[`🌐`](https://www.vmware.com/)
> - ` 👤 `︲**Interface Chaise-Clavier fonctionnelle.**
> - ` ☕ `︲**Un peu de patience !**

---

<a id="preparation-de-lenvironnement"></a>
## `🛠️`︲Préparation de l'environnement

---

<a id="installation-de-windows"></a>
### `💿`︲Installation de Windows 11 (client)

---

> [!WARNING]
> Prendre un snapshot de la VM après validation de cette configuration.

1️⃣︲**Configuration de la VM**  
   - **Disque :** 80 Go  
   - **RAM :** 4 Go  
   - **CPU :** 2 cœurs  

<details>
  <summary>📸︲Configuration initiale (VMware)</summary>

---

<img width="761" height="733" alt="Screenshot_29" src="https://github.com/user-attachments/assets/8e838f92-9bf5-445a-b6e1-61ea1c5d9e1b" />

Sur cette capture, on peut voir la **configuration de la mémoire de la VM sous VMware**.  
Il faut régler la mémoire à **4096 Mo (4 Go)**, soit en utilisant le curseur, soit en entrant la valeur manuellement.  
Enfin, cliquer sur **OK** pour valider les paramètres et sauvegarder la configuration.

---
</details>

---

2️⃣︲**Installation depuis l’ISO**  
   - Sélectionner langue, clavier et région  

<details>
  <summary>📸︲Sélection clavier et installation</summary>

  ---
  <img width="1022" height="769" alt="Screenshot_2" src="https://github.com/user-attachments/assets/4013d7fe-1cf0-4e5c-8d7d-b4cf663a85e1" />

  Sur cette capture, on peut voir la **sélection du clavier**.  
  Il faut s’assurer que la méthode d’entrée est **Français (Traditionnel, AZERTY)** avant de cliquer sur *Suivant*.

  ---
  <img width="1026" height="771" alt="Screenshot_3" src="https://github.com/user-attachments/assets/4b8cf19c-df8b-443c-9127-bc6d3805b8a7" />

  Sur cette capture, on peut voir le **type d’installation**.  
  Il faut choisir *Installer Windows 11* et cocher la suppression de tous les fichiers, applications et paramètres avant de cliquer sur *Suivant*.

</details>

---

3️⃣︲**Création de l’utilisateur**  
   - **Nom :** `btssio`  
   - **Mot de passe :** `btssio`  

<details>
  <summary>📸︲Création de l’utilisateur</summary>

<img width="1022" height="769" alt="Screenshot_11" src="https://github.com/user-attachments/assets/603eca66-704a-4aa0-8b73-7ed9f5db21c1" />

➡️ Entrer le **nom d’utilisateur `btssio`**, cliquer sur **Suivant**

<img width="1024" height="770" alt="Screenshot_13" src="https://github.com/user-attachments/assets/73800d3f-d047-4310-91e1-c5b03380349b" />

➡️ Entrer le **mot de passe `btssio`** et confirmer  

</details>

<details>
  <summary>📸︲OPTIONEL CHOIX OOBE</summary>
  
<img width="1026" height="770" alt="Screenshot_18" src="https://github.com/user-attachments/assets/4004e27f-c2c2-46b7-9460-b3ddda233c92" />
<img width="1022" height="771" alt="Screenshot_17" src="https://github.com/user-attachments/assets/720c73cd-2ad4-465e-b58a-ca5906f895f3" />
<img width="1027" height="771" alt="Screenshot_16" src="https://github.com/user-attachments/assets/592a58d9-d7e7-4497-b808-62d184f0e42f" />
<img width="994" height="771" alt="Screenshot_15" src="https://github.com/user-attachments/assets/6cd89070-4682-46e5-9c8d-714d89b30ec8" />
<img width="1026" height="770" alt="Screenshot_14" src="https://github.com/user-attachments/assets/3ac9e60f-a7db-4ad0-ba02-7af20f2f2ee9" />

</details>

---

<a id="installation-de-windows-server"></a>
### `💿`︲Installation de Windows Server 2025 (serveur)

> [!WARNING]
> Prendre un snapshot de la VM après validation de cette configuration.

---

1️⃣︲**Configuration de la VM**  
   - Disque : **80 Go**  
   - RAM : **2 Go**  
   - CPU : **2 cœurs**

<details>
  <summary>📸︲Configuration initiale serveur</summary>

<img width="759" height="731" alt="Screenshot_31" src="https://github.com/user-attachments/assets/09f78ba3-4e73-4579-b685-746b19399063" />

Vérifier que disque, RAM et CPU sont corrects avant l’installation.

</details>

---

2️⃣︲**Partitionnement du disque**  
   - 40 Go pour l’OS  
   - 40 Go pour DATA  

<details>
  <summary>📸︲Partitionnement</summary>

<img width="1022" height="772" alt="Screenshot_5" src="https://github.com/user-attachments/assets/3d76f21a-6dca-4641-903a-3f5ddcb6db0f" />

Créer deux partitions : 40 Go pour l’OS et 40 Go pour les données.

</details>

---

3️⃣︲**Installation depuis l’ISO**  
   - Sélectionner langue, clavier et région  

<details>
  <summary>📸︲Sélection ISO serveur</summary>

<img width="1018" height="771" alt="Screenshot_1" src="https://github.com/user-attachments/assets/0a8564ef-ff3f-43d4-ba0c-2fbee5e9de43" />
<img width="1026" height="767" alt="Screenshot_19" src="https://github.com/user-attachments/assets/e36dceae-aa06-4a4b-ba8d-cc3a935823ba" />

Choisir langue Français et clavier pour le serveur.  

</details>

---

4️⃣︲**Sélection de la méthode d’installation**  
   - Choisir **Installation personnalisée** (Custom Install)  
   - Sélectionner **Méthode de licence** et entrer la **clé produit**  
   - Sélectionner l’image : **Windows Server 2025 Standard (expérience utilisateur)**  

<details>
  <summary>📸︲Méthode d’installation et image</summary>

<img width="1026" height="774" alt="Screenshot_2" src="https://github.com/user-attachments/assets/dff9d49b-90ce-418f-bf61-931849ae3b6b" />
Vérifier la méthode d’installation, entrer la clé produit et choisir l’image correcte.

<img width="1026" height="770" alt="Screenshot_3" src="https://github.com/user-attachments/assets/350e3289-aca5-4c5b-8440-e6a4807825fb" />
Entrer la **clé produit**.

<img width="1022" height="773" alt="Screenshot_4" src="https://github.com/user-attachments/assets/f96bac0c-f279-4a23-b65e-b9f92ebd888d" />
Sélectionner l’image : **Windows Server 2025 Standard (expérience utilisateur)**

<img width="1019" height="768" alt="Screenshot_6" src="https://github.com/user-attachments/assets/b09467b8-122a-407d-913d-1b060b14b1c5" />


</details>

---

5️⃣︲**Création du compte administrateur**  
   - Nom : `Administrateur`  
   - Mot de passe : `btssio-lmc25`
   
**Enregistrer le couple login/mot de passe (Administrateur / btssio-lmc25) dans la description de la VM.**

---

6️⃣︲**Configuration réseau**  
   - IP : `172.16.0.1`  
   - Masque : `255.255.255.0`  

<details>
  <summary>📸︲Paramètres réseau serveur</summary>

<img width="1024" height="769" alt="Screenshot_11" src="https://github.com/user-attachments/assets/d8ecdf27-9dfd-4eb5-8405-c74a969fc1e8" />
Configurer IP et masque pour le serveur.

</details>

> [!WARNING]
> Prendre un snapshot de la VM après validation de cette configuration.

---

7️⃣︲**Vérification de l’installation**  
   - Redémarrer et se connecter avec le compte administrateur  

<details>
  <summary>📸︲Vérification finale serveur</summary>

<img width="1027" height="774" alt="Screenshot_30" src="https://github.com/user-attachments/assets/2d4565cd-66e0-454e-be4c-6f002718e385" />
Le serveur est prêt et l’administrateur peut se connecter !

</details>

---

<details>
  <summary><strong>💡︲Conseils pour Windows Server</strong></summary>

  **Vérifiez que la partition `DATA` est correctement créée et détectée après l’installation.**
  
</details>

---

<a id="installation-et-configuration-du-controleur-de-domaine"></a>
### `🏛️`︲Installation et configuration du contrôleur de domaine
---

<a id="installation-roles-ad-ds-et-dns"></a>
### `🔧`︲Installation des rôles AD DS et DNS...

---

1️⃣ ︲**Accéder à l’ajout de rôles et fonctionnalités**

Ouvrez le Gestionnaire de serveur.

Dans le Tableau de bord, cliquez sur Gérer.

Sélectionnez ensuite Ajouter des rôles et des fonctionnalités.
<details>
  <summary><strong>💡︲Captures d'écran</strong></summary>
  <img width="1029" height="773" alt="Screenshot_10" src="https://github.com/user-attachments/assets/b8bcf212-d61f-4e17-b618-cf23f5ad5e82" />

</details>

---

2️⃣︲**Lancer l’assistant d’ajout de rôles et de fonctionnalités**

La fenêtre Assistant Ajout de rôles et de fonctionnalités s’ouvre automatiquement.

Cliquez sur Suivant pour continuer.
<details>
  <summary><strong>💡︲Captures d'écran</strong></summary>
<img width="1027" height="767" alt="Screenshot_1" src="https://github.com/user-attachments/assets/59314f25-34eb-4084-8768-34021fd2179b" />
</details>

---

3️⃣︲**Choisir l'installation basée sur un rôle ou une fonctionnalité**

Dans la fenêtre suivante, sélectionnez Installation basée sur un rôle ou une fonctionnalité.

Vous verrez une liste avec des options sous forme de puces.

Cliquez sur Suivant pour continuer.
<details>
  <summary><strong>💡︲Captures d'écran</strong></summary>
<img width="1028" height="767" alt="Screenshot_2" src="https://github.com/user-attachments/assets/974e4085-45c6-4ebd-8d84-9572d2f404f9" />
</details>

---

4️⃣︲**Choisir le serveur pour l'installation**

L’assistant vous demande ensuite où installer la fonctionnalité.

Cliquez sur Sélectionner un serveur du pool de serveurs.

Dans la liste, choisissez le serveur `SRV-AD1`.
<details>
  <summary><strong>💡︲Captures d'écran</strong></summary>
<img width="1025" height="773" alt="Screenshot_3" src="https://github.com/user-attachments/assets/1f1a653f-6a8f-4934-8ee9-87679b9f353d" />
</details>

---

5️⃣︲**Sélectionner les fonctionnalités à installer**

Un menu s'ouvre avec des cases à cocher pour sélectionner les fonctionnalités.

Cherchez et cochez la fonctionnalité Service de domaine Active Directory.

Une nouvelle fenêtre s'ouvre.

Cochez la case Inclure les outils de gestion, si applicable (cette option est cochée par défaut).

Cliquez sur Ajouter des fonctionnalités.

Et ensuite faire "Suivant"
<details>
  <summary><strong>💡︲Captures d'écran</strong></summary>
<img width="1025" height="773" alt="Screenshot_4" src="https://github.com/user-attachments/assets/1d7493b3-89ad-4107-b894-4e9979339b02" />
   
---

<img width="1026" height="771" alt="Screenshot_5" src="https://github.com/user-attachments/assets/4b8aab9d-6982-4250-94f9-b055739aa7f0" />
</details>

---

6️⃣︲**Confirmer et lancer l'installation**

Vérifiez que toutes les options d'installation sont correctes pour éviter toute erreur.

Une fois la vérification effectuée, cliquez sur Suivant pour commencer l'installation du rôle.

L'installation prendra quelques minutes.

Une fois terminée, il sera nécessaire de redémarrer le serveur pour appliquer les changements.

<details>
  <summary><strong>💡︲Captures d'écran</strong></summary>
   <img width="1024" height="770" alt="Screenshot_7" src="https://github.com/user-attachments/assets/afa101e0-3f52-4df5-92df-7f4ea79750fb" />
   <img width="1025" height="771" alt="Screenshot_8" src="https://github.com/user-attachments/assets/624efe48-fd2b-4425-848f-23b69dff1f2a" />
   <img width="1027" height="770" alt="Screenshot_9" src="https://github.com/user-attachments/assets/1b5b2339-2f70-4f99-809f-c5bf919d4da6" />
</details>

---

## ` ✅ `︲Conclusion et Annexes

* d’un **client Windows 11 prêt à joindre un domaine**
* d’un **serveur Windows Server 2025 propre**
* du rôle **AD DS**
* du rôle **DNS**
* d’un domaine **entièrement fonctionnel**
* d’un environnement propre, reproductible et exploitable pour la suite (GPO, comptes, stratégies, automatisations).


---

## `🧰`︲Outils et Ressources utilisés pour la création de cette documentation.

* Windows 11
* Windows Server 2025
* VMware.
* PowerShell
* Documentation Microsoft (AD, DNS, domaine)

---

Ce dépôt présente un guide **complet, structuré et pédagogique**, destiné à installer :

* un **client Windows 11**
* un **serveur Windows Server 2025**
* un **contrôleur de domaine Active Directory**
* le **service DNS** associé
* la **promotion du serveur en domaine `descartesbleu.org`**

L’objectif est d’avoir un environnement fonctionnel, propre et conforme aux pratiques professionnelles SISR.

---

## `📑`︲Sommaire

1. [`📘`︲Introduction](#introduction)

   * [`❔`︲Contexte & objectifs](#contexte-objectifs)
   * [`🧰`︲Architecture & outils utilisés](#architecture-outils)

2. [`🛠️`︲Préparation de l’environnement](#preparation-environnement)

   * [`💿`︲Installation du client Windows 11](#installation-windows11)
   * [`💿`︲Installation de Windows Server 2025](#installation-windowsserver)

3. [`🏛️`︲Installation et configuration du contrôleur de domaine](#installation-controleur-domaine)

   * [`🔧`︲Installation des rôles AD DS & DNS](#installation-ad-ds-dns)
   * [`🌐`︲Promotion en contrôleur de domaine et création du domaine](#promotion-domaine)

4. [`📚`︲Conclusion](#conclusion)

5. [`🧰`︲Outils & Ressources](#outils-ressources)

---

<a id="introduction"></a>
# `📘`︲Introduction

---

<a id="contexte-objectifs"></a>
### `❔`︲Contexte et objectifs du TP

> [!NOTE]
> Dans ce TP, tu vas apprendre à :
>
> * installer un système client (Windows 11) et un serveur (Windows Server 2025)
> * configurer un **contrôleur de domaine**
> * intégrer un **service DNS**
> * comprendre le fonctionnement d’un domaine Active Directory
> * créer et gérer des **utilisateurs**, **groupes** et **stratégies de groupe (GPO)**
> * manipuler PowerShell pour automatiser certaines tâches
>
> **Objectif principal :**
> Obtenir un environnement d’administration réseau complet, stable et fonctionnel, tel qu’attendu dans un contexte SIO SISR.

---

<a id="architecture-outils"></a>
### `🧰`︲Architecture réseau & outils utilisés



---

<a id="preparation-environnement"></a>
# `🛠️`︲Préparation de l’environnement

---

<a id="installation-windows11"></a>
## `💿`︲Installation du client Windows 11

> [!WARNING]
> **IMPORTANT :** Prendre un **snapshot** de la VM après configuration de base.

---

### 1️⃣︲Configuration de la machine virtuelle

* Disque : **80 Go**
* RAM : **4 Go**
* CPU : **2 cœurs**

<details>
  <summary>📸︲Configuration initiale (Windows 11)</summary>

*(Les captures d’origine sont conservées, conformes au TP.)*

</details>

---

### 2️⃣︲Installation depuis l’ISO

* Sélectionner : langue, format horaire, clavier
* Procéder à l’installation propre

<details>
  <summary>📸︲Sélection du clavier</summary>

*(Captures originales)*

</details>

---

### 3️⃣︲Création du compte local

* Nom : `btssio`
* Mot de passe : `btssio`

<details>
  <summary>📸︲Création du compte local</summary>

*(Captures originales)*

</details>

---

### (Optionnel) Configuration OOBE

<details>
  <summary>📸︲Choix OOBE (optionnel)</summary>

*(Captures originales)*

</details>

---

<a id="installation-windowsserver"></a>
## `💿`︲Installation de Windows Server 2025 (Serveur)

---

> [!WARNING]
> Faire un **snapshot** après configuration initiale.

---

### 1️⃣︲Configuration de la VM

* Disque : **80 Go**
* RAM : **2 Go**
* CPU : **2 cœurs**

<details>
  <summary>📸︲Configuration serveur</summary>

*(Captures originales)*

</details>

---

### 2️⃣︲Partitionnement

* `40 Go` pour l’OS
* `40 Go` pour DATA

<details>
  <summary>📸︲Partitionnement</summary>

*(Captures originales)*

</details>

---

### 3️⃣︲Installation de l’OS depuis l’ISO

* Langue : FR
* Clavier : FR
* Sélectionner édition **Windows Server 2025 Standard (Expérience utilisateur)**

<details>
  <summary>📸︲Choix ISO + Image</summary>

*(Captures originales)*

</details>

---

### 4️⃣︲Création du compte Administrateur

* Nom : `Administrateur`
* Mot de passe : `btssio-lmc25`

> [!IMPORTANT]
> **Note le couple identifiants/mot de passe dans la description de la VM.**

---

### 5️⃣︲Configuration réseau

* IP : `172.16.0.1`
* Masque : `255.255.255.0`

<details>
  <summary>📸︲Paramètres réseau</summary>

*(Captures originales)*

</details>

---

### 6️⃣︲Vérification & démarrage

* Redémarrer
* Se connecter avec le compte admin

<details>
  <summary>📸︲Fin d’installation</summary>

*(Captures originales)*

</details>

---

<a id="installation-controleur-domaine"></a>
# `🏛️`︲Installation et configuration du contrôleur de domaine

---

<a id="installation-ad-ds-dns"></a>
## `🔧`︲Installation des rôles AD DS & DNS

---

### 1️⃣︲Accès à “Ajouter des rôles et fonctionnalités”

<details>
  <summary>📸︲Gestionnaire de serveur</summary>

*(Captures originales)*

</details>

---

### 2️⃣︲Sélection du rôle AD DS

* Cocher : **Services de domaine Active Directory**
* Ajouter les outils associés
* Valider

<details>
  <summary>📸︲Sélection AD DS</summary>

*(Captures originales)*

</details>

---

### 3️⃣︲Sélection du rôle DNS

* Cocher : **DNS Server**
* Ajouter les outils
* Valider

<details>
  <summary>📸︲Sélection DNS</summary>

*(Captures originales)*

</details>

---

### 4️⃣︲Confirmation & installation

> [!NOTE]
> L’installation prend quelques minutes, puis propose la **promotion du serveur**.

<details>
  <summary>📸︲Avancement installation</summary>

*(Captures originales)*

</details>

---

<a id="promotion-domaine"></a>
## `🌐`︲Promotion du serveur en contrôleur de domaine

---

### 1️⃣︲Promouvoir en contrôleur de domaine

* Choisir : **Ajouter une nouvelle forêt**
* Nom de domaine racine :

```
descartesbleu.org
```

<details>
  <summary>📸︲Création forêt + domaine</summary>

*(Captures originales)*

</details>

---

### 2️⃣︲Configuration fonctionnelle de AD DS

* Mot de passe DSRM
* Vérifications
* Installation automatique du DNS

---

### 3️⃣︲Redémarrage final

> [!TIP]
> Après redémarrage, ton serveur est **contrôleur de domaine opérationnel**.
