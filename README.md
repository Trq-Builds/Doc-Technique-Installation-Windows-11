# ` 🪟 `︲Doc-Technique-Installation-Windows-11

---

Ce dépôt GitHub met à disposition une documentation claire et complète pour réaliser une installation propre de Windows 11 en machine virtuelle, grâce à un guide structuré étape par étape et illustré de captures d’écran pour faciliter la compréhension.

---

## ` 📑 `︲Sommaire (cliquez pour accéder directement à la section souhaitée)

1. [` 🟦 `︲Introduction.](#introduction)
   - [` 🧰 `︲Prérequis & outils nécessaires.](#prérequis--outils-nécessaires)

2. [` 💾 `︲Téléchargement & Préparation des fichiers.](#téléchargement--préparation-des-fichiers)
   - [` 🌐 `︲Téléchargement officiel de l'ISO Windows 11.](#téléchargement-officiel-de-liso-windows-11)
   - [` 🧲 `︲Vérification de l'intégrité de l'ISO (SHA256).](#vérification-de-lintégrité-de-liso-sha256)
   - [` 🗂️ `︲Organisation des fichiers pour la VM.](#organisation-des-fichiers-pour-la-vm)

3. [` 🛠️ `︲Configuration de la machine virtuelle.](#configuration-de-la-machine-virtuelle)
   - [` ⚙️ `︲Paramètres matériels : RAM, CPU, Disque.](#paramètres-matériels--ram-cpu-disque)
   - [` 🧩 `︲Configuration réseau : DHCP / NAT / Bridge.](#configuration-réseau--dhcp--nat--bridge)
   - [` 📎 `︲Ajout de l'ISO dans le lecteur virtuel.](#ajout-de-liso-dans-le-lecteur-virtuel)
   - [` 🛡️ `︲Paramètres UEFI / Secure Boot / TPM virtuel.](#paramètres-uefi--secure-boot--tpm-virtuel)

4. [` 💿 `︲Installation de Windows 11.](#installation-de-windows-11)
   - [` 🌍 `︲Choix de la langue, région & clavier.](#choix-de-la-langue-région--clavier)
   - [` 🧱 `︲Partitionnement du disque virtuel.](#partitionnement-du-disque-virtuel)
   - [` 🚀 `︲Lancement de l'installation.](#lancement-de-linstallation)

5. [` 👤 `︲Configuration OOBE (Out-of-Box Experience).](#configuration-oobe-out-of-box-experience)
   - [` 👤 `︲Création du compte utilisateur local.](#création-du-compte-utilisateur-local)
   - [` 🔐 `︲Mot de passe & questions de sécurité.](#mot-de-passe--questions-de-sécurité)
   - [` 🌐 `︲Connexion / Non-connexion à Internet.](#connexion--non-connexion-à-internet)
   - [` 📊 `︲Confidentialité & Paramètres optionnels.](#confidentialité--paramètres-optionnels)
   - [` 🎛️ `︲Paramètres OOBE avancés (optionnel).](#paramètres-oobe-avancés-optionnel)

6. [` 🧼 `︲Post-Installation Immédiate (VM).](#post-installation-immédiate-vm)
   - [` 🔄 `︲Mise à jour Windows Update.](#mise-à-jour-windows-update)
   - [` 🧩 `︲Installation des VMware Tools / Additions virtuelles.](#installation-des-vmware-tools--additions-virtuelles)
   - [` 🚫 `︲Désactivation des options inutiles (télémétrie, suggestions, pubs).](#désactivation-des-options-inutiles)
   - [` 🔐 `︲Vérification du compte & options de sécurité.](#vérification-du-compte--options-de-sécurité)

7. [` ✅ `︲Conclusion & Annexes.](#conclusion-et-annexes)

8. [` 🧰 `︲Outils & Ressources utilisés.](#outils--ressources-utilisés)

---

> [!IMPORTANT]
> * **Les captures d’écran seront ajoutées progressivement !**
> * **Si une image est peu lisible dans le menu, il suffit de cliquer dessus. L'image s'ouvrira dans un nouvel onglet, vous permettant ainsi de la consulter en taille réelle et d'utiliser la fonction zoom !**

---

> [!TIP]
> - **Pour afficher les captures d’écran, clique sur le menu déroulant avec l’émoji : `  📸  `.**
> - **Le menu s’ouvrira et affichera la ou les captures d’écran !**

---

<a id="introduction"></a>

## ` 🟦 `︲Introduction

<a id="prérequis--outils-nécessaires"></a>

### ` 🧰 `︲Prérequis & outils nécessaires

> [!IMPORTANT]
> - `🌐`︲**ISO Windows 11**︲[`🌐`](https://www.microsoft.com/fr-fr/software-download/windows11)
>   
> - ` 📦 `︲**VMWare :** ︲[`🌐`](https://www.vmware.com/)
>   
> - `👤`︲**Interface Chaise-Clavier**
> 
> - `☕`︲**Patience**

---

> [!NOTE]
> Cette documentation couvre **100% du cycle d'installation** d'un Windows 11 en machine virtuelle :
> - Téléchargement de l'ISO  
> - Configuration de la VM  
> - Installation complète de l'OS  
> - Passage OOBE  
> - Post-installation immédiate  
> - Vérifications finales

---

<a id="téléchargement--préparation-des-fichiers"></a>

## ` 💾 `︲Téléchargement & Préparation des fichiers

<a id="téléchargement-officiel-de-liso-windows-11"></a>

### ` 🌐 `︲Téléchargement officiel de l'ISO Windows 11

---

Pour garantir une installation **fiable, sécurisée et conforme**, il est impératif d’utiliser **exclusivement l’ISO officielle fournie par Microsoft**.

1. Se rendre sur le site officiel de Microsoft dédié au téléchargement de Windows 11.
2. Dans la section **“Télécharger l’image disque (ISO) de Windows 11”**, sélectionner :

   * **Édition :** *Windows 11 (multi-édition)*
3. Cliquer sur **Télécharger** puis choisir :

   * **Langue du produit :** *Français*
4. Valider et lancer le téléchargement du fichier **ISO**.

> [!IMPORTANT]
>
> * Le fichier téléchargé est une **image disque complète** contenant l’ensemble des composants nécessaires à l’installation de Windows 11.
> * La taille de l’ISO est généralement comprise entre **5 et 6 Go** selon la version !

> [!NOTE]
> Le téléchargement peut prendre plusieurs minutes selon la vitesse de la connexion Internet.

---

🛑 **Ne pas extraire l’ISO**
L’image disque doit être **conservée telle quelle**. Elle sera montée directement dans la machine virtuelle lors des étapes suivantes.

---

<a id="vérification-de-lintégrité-de-liso-sha256"></a>

### ` 🧲 `︲Vérification de l'intégrité de l'ISO (SHA256) (Optionel)

---

Après le téléchargement, il est **fortement recommandé** de vérifier l’intégrité de l’ISO afin de s’assurer que le fichier n’est **ni corrompu ni altéré**.

Cette vérification repose sur le calcul de l’empreinte **SHA256** du fichier ISO, puis sa comparaison avec la valeur officielle fournie par Microsoft.

#### Méthode via PowerShell (Windows)

1. Ouvrir **PowerShell**.
2. Se placer dans le dossier contenant l’ISO ou utiliser le chemin complet.
3. Exécuter la commande suivante :

```powershell
Get-FileHash .\Win11_x64.iso -Algorithm SHA256
```

4. Noter la valeur retournée dans la colonne **Hash**.

#### Comparaison

* Comparer l’empreinte obtenue avec le **SHA256 officiel** communiqué par Microsoft.
* Si les deux valeurs sont **strictement identiques**, le fichier est **intègre et exploitable**.

> [!IMPORTANT]
>
> * **Une seule différence** dans le hash indique un fichier invalide.
> * En cas de mismatch, **supprimer l’ISO** et le retélécharger.

> [!NOTE]
> Cette étape permet d’éviter des erreurs d’installation, des comportements instables ou des échecs lors du déploiement de la machine virtuelle.

---


<a id="organisation-des-fichiers-pour-la-vm"></a>

### ` 🗂️ `︲Organisation des fichiers pour la VM

*(sections à compléter)*

---

<a id="configuration-de-la-machine-virtuelle"></a>

## ` 🛠️ `︲Configuration de la machine virtuelle

<a id="paramètres-matériels--ram-cpu-disque"></a>

### ` ⚙️ `︲Paramètres matériels : RAM, CPU, Disque

* ` 📡 `︲Adressage IP : **`DHCP`**
  
* ` 📏 `︲Mémoire : **`4096Mo`**
  
* ` 💾 `︲Disque : **`80Go`** (dynamique)
  
* ` ❤️ `︲Cœurs : **`2`**

<details>
  <summary>📸︲Configuration initiale (VMware)</summary>

---

<img width="761" height="733" src="https://github.com/user-attachments/assets/8e838f92-9bf5-445a-b6e1-61ea1c5d9e1b" />

*(Réglage de la mémoire : 4096 Mo puis valider avec OK.)*

---

</details>

<a id="configuration-réseau--dhcp--nat--bridge"></a>

### ` 🧩 `︲Configuration réseau : DHCP / NAT / Bridge

*(sections à compléter)*

<a id="ajout-de-liso-dans-le-lecteur-virtuel"></a>

### ` 📎 `︲Ajout de l'ISO dans le lecteur virtuel

*(sections à compléter)*

<a id="paramètres-uefi--secure-boot--tpm-virtuel"></a>

### ` 🛡️ `︲Paramètres UEFI / Secure Boot / TPM virtuel

*(sections à compléter)*

---

<a id="installation-de-windows-11"></a>

## ` 💿 `︲Installation de Windows 11

<a id="choix-de-la-langue-région--clavier"></a>

### ` 🌍 `︲Choix de la langue, région & clavier

- Sélectionner langue, clavier et région

<details>
  <summary>📸︲Sélection clavier et installation</summary>

---

<img width="1022" height="769" src="https://github.com/user-attachments/assets/4013d7fe-1cf0-4e5c-8d7d-b4cf663a85e1" />

*(Sélectionner **Français (AZERTY)** puis cliquer sur Suivant.)*

---

<img width="1026" height="771" src="https://github.com/user-attachments/assets/4b8cf19c-df8b-443c-9127-bc6d3805b8a7" />

*(Choisir **Installer Windows 11**.)*

---

</details>

<a id="partitionnement-du-disque-virtuel"></a>

### ` 🧱 `︲Partitionnement du disque virtuel

*(sections à compléter)*

<a id="lancement-de-linstallation"></a>

### ` 🚀 `︲Lancement de l'installation

*(sections à compléter)*

---

<a id="configuration-oobe-out-of-box-experience"></a>

## ` 👤 `︲Configuration OOBE (Out-of-Box Experience)

<a id="création-du-compte-utilisateur-local"></a>

### ` 👤 `︲Création du compte utilisateur local

- **Nom :** `btssio`  
- **Mot de passe :** `btssio`

<details>
  <summary>📸︲Création de l'utilisateur</summary>

---

<img width="1022" height="769" src="https://github.com/user-attachments/assets/603eca66-704a-4aa0-8b73-7ed9f5db21c1" />

➡️ Entrer le nom d'utilisateur **btssio**.

---

<img width="1024" height="770" src="https://github.com/user-attachments/assets/73800d3f-d047-4310-91e1-c5b03380349b" />

➡️ Entrer le mot de passe **btssio**.

---

</details>

<a id="mot-de-passe--questions-de-sécurité"></a>

### ` 🔐 `︲Mot de passe & questions de sécurité

*(sections à compléter)*

<a id="connexion--non-connexion-à-internet"></a>

### ` 🌐 `︲Connexion / Non-connexion à Internet

*(sections à compléter)*

<a id="confidentialité--paramètres-optionnels"></a>

### ` 📊 `︲Confidentialité & Paramètres optionnels

*(sections à compléter)*

<a id="paramètres-oobe-avancés-optionnel"></a>

### ` 🎛️ `︲Paramètres OOBE avancés (optionnel)

<details>
  <summary>📸︲OPTIONNEL — Choix OOBE</summary>

<img width="1026" height="770" src="https://github.com/user-attachments/assets/4004e27f-c2c2-46b7-9460-b3ddda233c92" />
<img width="1022" height="771" src="https://github.com/user-attachments/assets/720c73cd-2ad4-465e-b58a-ca5906f895f3" />
<img width="1027" height="771" src="https://github.com/user-attachments/assets/592a58d9-d7e7-4497-b808-62d184f0e42f" />
<img width="994" height="771" src="https://github.com/user-attachments/assets/6cd89070-4682-46e5-9c8d-714d89b30ec8" />
<img width="1026" height="770" src="https://github.com/user-attachments/assets/3ac9e60f-a7db-4ad0-ba02-7af20f2f2ee9" />

</details>

---

<a id="post-installation-immédiate-vm"></a>

## ` 🧼 `︲Post-Installation Immédiate (VM)

<a id="mise-à-jour-windows-update"></a>

### ` 🔄 `︲Mise à jour Windows Update

*(sections à compléter)*

<a id="installation-des-vmware-tools--additions-virtuelles"></a>

### ` 🧩 `︲Installation des VMware Tools / Additions virtuelles

*(sections à compléter)*

<a id="désactivation-des-options-inutiles"></a>

### ` 🚫 `︲Désactivation des options inutiles (télémétrie, suggestions, pubs)

*(sections à compléter)*

<a id="vérification-du-compte--options-de-sécurité"></a>

### ` 🔐 `︲Vérification du compte & options de sécurité

*(sections à compléter)*

---

<a id="conclusion-et-annexes"></a>

## ` ✅ `︲Conclusion et Annexes

*(sections à compléter)*

---

<a id="outils--ressources-utilisés"></a>

## ` 🧰 `︲Outils & Ressources utilisés

* ` 🌐 `︲Liens annexes :  
  * X [`🌐`]()  
  * X [`🌐`]()  
  * X [`🌐`]()
  * X [`🌐`]()
  * X [`🌐`]()

---

* ` 🤖 `︲**GPT-5.1** ︲ [`🌐`](https://chatgpt.com/)
  
* ` ❓ `︲**Markdownguide.org** ︲ [`🌐`](https://www.markdownguide.org/)
  
* ` 🤖 `︲**NotebookLM** ︲ [`🌐`](https://notebooklm.google.com/)
  
* ` ✂️ `︲**Screenpresso** ︲ [`🌐`](https://www.screenpresso.com/fr/)
  
* ` 😀 `︲**Smiley.cool** ︲ [`🌐`](https://smiley.cool/emoji-list.php)
  
* ` ❓ `︲**Syntaxe GitHub Markdown** ︲ [`🌐`](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

---

> ` ⏺️ `︲Nagi Player︲[`🌐`](https://github.com/Anthonyy232/Nagi)
> 
> ` ☕ `︲De la patience !

---
