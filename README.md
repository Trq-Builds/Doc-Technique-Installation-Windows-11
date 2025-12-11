# ` 🪟 `︲Doc-Technique-Installation-Windows-11

## ` 📑 `︲Sommaire (cliquez pour accéder directement à la section souhaitée)

1. [` 🟦 `︲Introduction.](#introduction)
   - [` 🎯 `︲Objectifs du TP.](#objectifs-du-tp)
   - [` 🧰 `︲Prérequis & outils nécessaires.](#prérequis--outils-nécessaires)

2. [` 💾 `︲Téléchargement & Préparation des fichiers.](#téléchargement--préparation-des-fichiers)
   - [` 🌐 `︲Téléchargement officiel de l’ISO Windows 11.](#téléchargement-officiel-de-liso-windows-11)
   - [` 🧲 `︲Vérification de l’intégrité de l’ISO (SHA256).](#vérification-de-lintégrité-de-liso-sha256)
   - [` 🗂️ `︲Organisation des fichiers pour la VM.](#organisation-des-fichiers-pour-la-vm)

3. [` 🛠️ `︲Configuration de la machine virtuelle.](#configuration-de-la-machine-virtuelle)
   - [` ⚙️ `︲Paramètres matériels : RAM, CPU, Disque.](#paramètres-matériels--ram-cpu-disque)
   - [` 🧩 `︲Configuration réseau : DHCP / NAT / Bridge.](#configuration-réseau--dhcp-nat-bridge)
   - [` 📎 `︲Ajout de l’ISO dans le lecteur virtuel.](#ajout-de-liso-dans-le-lecteur-virtuel)
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

7. [` 📝 `︲Validation du TP.](#validation-du-tp)
   - [` ✔️ `︲Objectifs atteints.](#objectifs-atteints)
   - [` 📸 `︲Captures obligatoires.](#captures-obligatoires)

8. [` ✅ `︲Conclusion et Annexes.](#conclusion-et-annexes)

9. [` 🧰 `︲Outils & Ressources utilisés.](#outils--ressources-utilisés)


---

> [!NOTE]
> Cette documentation couvre **100% du cycle d’installation** d’un Windows 11 en machine virtuelle :
> - Téléchargement de l’ISO.
> - Configuration de la VM.
> - Installation de l’OS.
> - Passage OOBE.
> - Post-installation immédiate.
> - Vérifications finales.

---

<a id="presentation-de-larchitecture-reseau-et-des-outils-utilises"></a>
> [!IMPORTANT]
> **Présentation des outils et prérequis :**
> - `🖥️`︲**Client :** Windows 11  
> - `🔧`︲**Outils :** VMware  
> - ` 📦 `︲**VMWare :** ︲[`🌐`](https://www.vmware.com/)  
> - ` 👤 `︲**Interface Chaise-Clavier fonctionnelle**  
> - ` ☕ `︲**Un peu de patience !**  

---

> [!IMPORTANT]
> * **Les captures d’écran seront ajoutées progressivement.**  
> * **Si une image est peu lisible dans le menu, cliquez dessus pour l'ouvrir en taille réelle (zoom possible).**

> [!TIP]
> - Cliquez sur le menu déroulant ` 📸 ` pour afficher les captures d’écran.

---

` ⚙️ `︲**Configuration de la VM :**

* ` 📡 `︲**Adressage IP :** dynamique (DHCP).  
* ` 📏 `︲**Mémoire :** `4096 Mo`.  
* ` 💾 `︲**Disque :** `80 Go` (allocation dynamique).  
* ` ❤️ `︲**Cœurs :** `2`.  

<details>
  <summary>📸︲Configuration initiale (VMware)</summary>

---

<img width="761" height="733" alt="Screenshot_29" src="https://github.com/user-attachments/assets/8e838f92-9bf5-445a-b6e1-61ea1c5d9e1b" />

Sur cette capture, on peut voir la **configuration de la mémoire de la VM sous VMware**.  
Il faut régler la mémoire à **4096 Mo (4 Go)** via le curseur ou en entrant la valeur manuellement.  
Puis valider avec **OK** pour sauvegarder la configuration.

---

</details>

---

2️⃣︲**Installation depuis l’ISO**  
   - Sélectionner langue, clavier et région

<details>
  <summary>📸︲Sélection clavier et installation</summary>

---

<img width="1022" height="769" src="https://github.com/user-attachments/assets/4013d7fe-1cf0-4e5c-8d7d-b4cf663a85e1" />

*(Sélection du clavier : choisir **Français (AZERTY)** et cliquer sur Suivant.)*

---

<img width="1026" height="771" src="https://github.com/user-attachments/assets/4b8cf19c-df8b-443c-9127-bc6d3805b8a7" />

*(Choix du type d’installation : sélectionner **Installer Windows 11**.)*

---

</details>

---

3️⃣︲**Création de l’utilisateur**  
   - **Nom :** `btssio`  
   - **Mot de passe :** `btssio`

<details>
  <summary>📸︲Création de l’utilisateur</summary>

---

<img width="1022" height="769" src="https://github.com/user-attachments/assets/603eca66-704a-4aa0-8b73-7ed9f5db21c1" />

➡️ Entrer le **nom d’utilisateur `btssio`** puis cliquer sur **Suivant**.

---

<img width="1024" height="770" src="https://github.com/user-attachments/assets/73800d3f-d047-4310-91e1-c5b03380349b" />

➡️ Entrer le **mot de passe `btssio`** et confirmer.

---

</details>

<details>
  <summary>📸︲OPTIONNEL — Choix OOBE</summary>

<img width="1026" height="770" alt="Screenshot_18" src="https://github.com/user-attachments/assets/4004e27f-c2c2-46b7-9460-b3ddda233c92" />
<img width="1022" height="771" alt="Screenshot_17" src="https://github.com/user-attachments/assets/720c73cd-2ad4-465e-b58a-ca5906f895f3" />
<img width="1027" height="771" alt="Screenshot_16" src="https://github.com/user-attachments/assets/592a58d9-d7e7-4497-b808-62d184f0e42f" />
<img width="994" height="771" alt="Screenshot_15" src="https://github.com/user-attachments/assets/6cd89070-4682-46e5-9c8d-714d89b30ec8" />
<img width="1026" height="770" alt="Screenshot_14" src="https://github.com/user-attachments/assets/3ac9e60f-a7db-4ad0-ba02-7af20f2f2ee9" />

</details>

---

## `🧰`︲Outils et Ressources utilisés pour la création de cette documentation :

---

* ` 🌐 `︲**Liens annexes :**
  * X [`🌐`]()
  * X [`🌐`]()
  * X [`🌐`]()
  
---

* ` 🤖 `︲GPT-5.1 [`🌐`](https://chatgpt.com/)  
* ` ❓ `︲Markdownguide.org [`🌐`](https://www.markdownguide.org/)  
* ` 🤖 `︲NotebookLM [`🌐`](https://notebooklm.google.com/)  
* ` ✂️ `︲Screenpresso [`🌐`](https://www.screenpresso.com/fr/)  
* ` 😀 `︲Smiley.cool [`🌐`](https://smiley.cool/emoji-list.php)  
* ` ❓ `︲Syntaxe GitHub Markdown [`🌐`](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

---

> ` ⏺️ `︲Nagi Player [`🌐`](https://github.com/Anthonyy232/Nagi)  
> ` ☕ `︲De la patience !  

---

# ` 🧰 `︲Prérequis & outils nécessaires

> [!IMPORTANT]
> - `🌐`︲ISO Windows 11  
> - `🖥️`︲VMware Workstation / VirtualBox  
> - `📦`︲Espace disque nécessaire  
> - `👤`︲Interface Chaise-Clavier  
> - `☕`︲Patience  

---

# ` 💾 `︲Téléchargement & Préparation des fichiers

*(sections à remplir ci-dessous)*

---

# ` 🛠️ `︲Configuration de la machine virtuelle

*(sections à compléter)*

---

# ` 💿 `︲Installation de Windows 11

*(sections à compléter)*

---

# ` 👤 `︲Configuration OOBE

*(sections à compléter)*

---

# ` 🧼 `︲Post-installation Immédiate

*(sections à compléter)*

---

# ` 📝 `︲Validation du TP

*(sections à compléter)*

---

# ` ✅ `︲Conclusion & Annexes

*(sections à compléter)*




