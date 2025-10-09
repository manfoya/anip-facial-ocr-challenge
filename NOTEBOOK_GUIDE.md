# Guide d'Utilisation du Notebook 3_ocr_fraud_detection.ipynb

## Objectif

Ce notebook résout la troisième tâche du challenge ANIP : détecter les fraudes et falsifications dans les documents d'identité officiels.

## Problème Résolu

Le notebook avait des problèmes d'organisation qui empêchaient son exécution complète avec "Run All". Tous ces problèmes ont été corrigés.

## Exécution du Notebook

Le notebook peut maintenant être exécuté de deux façons:

### 1. Exécution Complète (Recommandé)

```
Menu Jupyter: Cell > Run All
```

Cette option exécute toutes les cellules dans l'ordre, du début à la fin. C'est maintenant possible car toutes les dépendances sont correctement ordonnées.

### 2. Exécution Cellule par Cellule

Vous pouvez aussi exécuter les cellules une par une avec `Shift+Enter`. L'ordre d'exécution doit être respecté (de haut en bas).

## Structure du Notebook

Le notebook est organisé en 9 sections principales:

### Section 0: Introduction
- Présentation du problème
- Types de documents analysés
- Stratégie adoptée

### Section 1: Configuration de l'Environnement
- Définition des chemins de données
- Exploration de la structure des dossiers
- **Variables créées:** `TRAIN_DIR`, `TEST_DIR`, `document_types`

### Section 2: Analyse Exploratoire des Données (EDA)
- Construction du dataset principal
- Analyse de la distribution
- **Variables créées:** `df_train` (DataFrame principal avec toutes les images)

### Section 3: Analyse des Fichiers Ground Truth (GT)
- Analyse des annotations OCR de référence
- Identification des champs communs et spécifiques
- **Variables créées:** `gt_data`, `all_fields`

### Section 4: Analyse des Propriétés des Images
- Analyse des dimensions et formats
- Statistiques sur les images

### Section 5: Préparation du Split Train/Validation
- Split stratifié des données
- **Variables créées:** `X_train`, `X_val`, `y_train`, `y_val`

### Section 6: Visualisation
- Exemples d'images par type et classe
- Inspection visuelle des données

### Section 7: Analyse de la Distribution des Classes
- Distribution par type de document
- Analyse de l'équilibre des classes
- Visualisations

### Section 8: Modélisation OCR et Classification
Cette section est divisée en 5 sous-sections:

#### 8.1: Dataset PyTorch
- Import de PyTorch et bibliothèques associées
- Définition de la classe `DocumentDataset`
- Définition des transformations d'images
- **Variables créées:** `pytorch_available`, `DocumentDataset`, `train_transform`, `val_transform`, `device`

#### 8.2: Création des DataLoaders
- Création des datasets PyTorch
- Configuration des DataLoaders
- **Variables créées:** `train_dataset`, `val_dataset`, `train_loader`, `val_loader`

#### 8.3: Modèle de Classification
- Définition du modèle CNN (FraudDetectionModel)
- Configuration de l'optimiseur et du scheduler
- **Variables créées:** `FraudDetectionModel` (classe), `model`, `criterion`, `optimizer`, `scheduler`

#### 8.4: Fonction d'Entraînement
- Définition de la fonction `train_model`
- Gestion de l'entraînement et de la validation
- **Variables créées:** `train_model` (fonction)

#### 8.5: Entraînement du Modèle
- Exécution de l'entraînement
- Sauvegarde du modèle
- **Variables créées:** `trained_model`, `training_history`

### Section 9: Extraction OCR et Prédiction
Divisée en 2 sous-sections:

#### 9.1: Fonctions OCR
- Configuration d'EasyOCR
- Fonctions d'extraction de texte
- **Variables créées:** `ocr_reader_available`, `reader`, `extract_text_easyocr`, `extract_document_fields`

#### 9.2: Pipeline de Prédiction Complet
- Fonction de prédiction intégrée (classification + OCR)
- Génération du fichier de soumission
- **Variables créées:** `predict_document`, `generate_submission_format`

## Dépendances Importantes

Le notebook respecte maintenant l'ordre suivant pour les dépendances critiques:

```
df_train (Section 2)
  ↓
X_train, X_val (Section 5)
  ↓
pytorch_available, DocumentDataset, transforms (Section 8.1)
  ↓
train_loader, val_loader (Section 8.2)
  ↓
model, optimizer (Section 8.3)
  ↓
train_model function (Section 8.4)
  ↓
Training execution (Section 8.5)
  ↓
OCR and Prediction (Section 9)
```

## Points d'Attention

1. **Données requises:** Le notebook attend que les données soient dans `/kaggle/input/tache3-anip/`. Si vous utilisez un autre emplacement, modifiez la variable `DATA_ROOT` dans la Section 1.

2. **PyTorch:** Si PyTorch n'est pas installé, la Section 8 sera ignorée mais le notebook continuera à s'exécuter.

3. **EasyOCR:** Si EasyOCR n'est pas disponible, la Section 9 utilisera des valeurs par défaut.

4. **Mémoire GPU:** Le batch_size dans la Section 8.2 est configuré à 32. Réduisez-le si vous rencontrez des erreurs de mémoire.

## Modifications Apportées

Les changements suivants ont été effectués pour permettre l'exécution complète:

1. ✅ Installation des packages déplacée au début (après les imports de base)
2. ✅ Section 5 (Train/Val Split) repositionnée avant les Sections 6 et 7
3. ✅ Section 8 réorganisée: sous-sections dans l'ordre 8.1 → 8.2 → 8.3 → 8.4 → 8.5
4. ✅ Suppression des en-têtes dupliqués
5. ✅ Vérification de toutes les dépendances

## Résultat Attendu

Après exécution complète du notebook:

1. **Dataset analysé:** Distribution des classes, propriétés des images
2. **Modèle entraîné:** Classification de fraude documentaire
3. **Pipeline OCR:** Extraction de texte pour documents authentiques
4. **Soumission générée:** Fichier JSON avec les prédictions

## Support

Pour plus de détails sur la réorganisation, consultez le fichier `NOTEBOOK_REORGANIZATION.md`.
