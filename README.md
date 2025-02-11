# Convertisseur Texte-Audio Kokoro TTS et RVC

[![Français](https://img.shields.io/badge/Langue-Français-blue.svg)](./README.md)
[![English](https://img.shields.io/badge/Language-English-green.svg)](./README_EN.md)

[**Lire ce README en Anglais / Read this README in English**](./README_EN.md)

## Description

Ce projet est un convertisseur texte-audio qui utilise deux technologies puissantes :

*   **Kokoro TTS (Text-to-Speech):**  Pour la synthèse vocale de haute qualité à partir de texte.
*   **RVC (Retrieval-Based Voice Conversion):**  Pour convertir la voix synthétisée par Kokoro TTS en celle de différents personnages ou styles vocaux, en utilisant des modèles pré-entraînés.

L'interface utilisateur est construite avec Gradio, offrant une expérience interactive et facile à utiliser directement dans votre navigateur.

## Télécharger les Modèles Pré-entraînés (Requis)

**Avant de continuer, vous devez télécharger les modèles pré-entraînés nécessaires au fonctionnement du convertisseur.**  Ces modèles incluent les fichiers `.bin`, `.onnx`, `.index` et `.pth` et sont essentiels pour Kokoro TTS et RVC.

Vous pouvez les télécharger depuis Google Drive :

[**Télécharger les Modèles Pré-entraînés (Google Drive)**](https://drive.google.com/drive/folders/1G6O0FgyFdwVjn3rMoJZRbg6gC1OrkaI9?usp=sharing)

**Une fois téléchargé, assurez-vous de placer les fichiers correctement dans les dossiers appropriés de votre projet.**  Typiquement, les fichiers `.pth` et `.index` pour RVC vont dans `modelRVC/pth/` et `modelRVC/index/` respectivement, et les modèles Kokoro TTS (.bin, .onnx) dans le dossier `model_tts`.  

## Installation

Suivez ces étapes pour installer et exécuter le convertisseur texte-audio :

1.  **Installer Visual Studio Installer (Requis pour Windows):**
    *   Si vous êtes sur Windows, il est nécessaire d'installer Visual Studio Installer pour compiler certaines dépendances.
    *   Téléchargez Visual Studio Installer depuis [le site officiel de Microsoft](https://visualstudio.microsoft.com/fr/downloads/).  Choisissez de télécharger "Visual Studio Community".
    *   Exécutez le programme d'installation téléchargé.
    *   Dans l'installateur de Visual Studio, lors de la sélection des charges de travail, **cochez la case**  `✅ Développement Desktop en C++` (vous pourriez devoir faire défiler la liste pour la trouver).
    *   Continuez l'installation en suivant les instructions à l'écran.  Vous n'avez pas besoin de sélectionner d'autres charges de travail ou composants pour ce projet.
2.  **Télécharger le projet:**
    *   Téléchargez le fichier ZIP du dépôt GitHub.
3.  **Extraire l'archive:**
    *   Extrayez le contenu du fichier ZIP dans un dossier de votre choix.
    *   ajouter les modèles installé avec google drive
4.  **Créer un environnement Anaconda:**
    *   Si vous n'avez pas Anaconda installé, téléchargez-le et installez-le depuis [le site officiel d'Anaconda](https://www.anaconda.com/products/distribution).
    *   Ouvrez Anaconda Prompt ou votre terminal.
    *   Créez un nouvel environnement Anaconda nommé `kokoro_RVC` avec Python 3.10 en utilisant la commande suivante :
        ```bash
        conda create -n kokoro_RVC python=3.10
        ```
5.  **Activer l'environnement:**
    *   Activez l'environnement `kokoro_RVC` avec la commande :
        ```bash
        conda activate kokoro_RVC
        ```
6.  **Naviguer vers le dossier du projet:**
    *   Utilisez la commande `cd` pour vous déplacer dans le dossier où vous avez extrait le projet. Par exemple :
        ```bash
        cd chemin/vers/le/dossier/kokoro-rvc-converter
        ```
7.  **Installer les dépendances:**
    *   Exécutez la commande suivante pour installer toutes les bibliothèques Python nécessaires. Assurez-vous d'être toujours dans l'environnement `kokoro_RVC` et dans le dossier du projet :
        ```bash
        python.exe -m pip install -r requirement1.txt && pip install -r requirement2.txt
        ```
    *   **Note:**  Si vous êtes sur un système autre que Windows et que `python.exe` ne fonctionne pas, essayez simplement `python -m pip install -r requirement1.txt && pip install -r requirement2.txt`.
8.  **Exécuter l'application:**
    *   Lancez l'application en exécutant la commande :
        ```bash
        python main.py
        ```
    *   L'interface Gradio s'ouvrira automatiquement dans votre navigateur web.

## Utilisation

Une fois l'application lancée, vous pouvez utiliser l'interface Gradio pour :

*   **Synthétiser de la parole avec Kokoro TTS** à partir de texte.
*   **Convertir la voix** en utilisant des modèles RVC, en appliquant un changement de ton (pitch shift).
*   **Combiner les deux** en générant de la parole TTS et en la convertissant en voix RVC en une seule étape.

Amusez-vous avec le convertisseur texte-audio !

## Modèles de Voix RVC

Vous pouvez trouver une grande variété de modèles de voix RVC pré-entraînés sur [weights.gg](https://www.weights.gg/).

Pour utiliser ces modèles avec ce convertisseur :

1.  **Téléchargez** les fichiers `.pth` et `.index` du modèle de voix RVC que vous souhaitez utiliser depuis [weights.gg](https://www.weights.gg/).
2.  **Placez** le fichier `.pth` dans le dossier `modelRVG/pth/` de votre projet. Créez le dossier `pth` s'il n'existe pas déjà.
3.  **Placez** le fichier `.index` dans le dossier `modelRVG/index/` de votre projet. Créez le dossier `index` s'il n'existe pas déjà.
4.  **Relancez** l'application `python main.py`. Les nouveaux modèles de voix RVC devraient maintenant apparaître dans les listes déroulantes de l'interface Gradio.

## Sources

Ce projet utilise les ressources suivantes :

*   **Kokoro-onnx:** [https://github.com/thewh1teagle/kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx) - Implémentation ONNX du modèle Kokoro TTS.
*   **Kokoro-82M version 1.0:** [https://huggingface.co/hexgrad/Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M) - Modèle Kokoro TTS pré-entraîné sur Hugging Face.
*   **rvc-python:** [https://github.com/daswer123/rvc-python](https://github.com/daswer123/rvc-python) - Librairie Python pour la conversion vocale RVC.

---

N'hésitez pas à contribuer à ce projet ou à signaler des problèmes.
