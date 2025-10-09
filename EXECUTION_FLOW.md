# Notebook Execution Flow Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│  PARTIE 1: CONFIGURATION & ANALYSE EXPLORATOIRE (Cellules 1-15)    │
└─────────────────────────────────────────────────────────────────────┘
  │
  ├─► [1] Titre: "Détection de Fraude dans les Documents d'Identité"
  │
  ├─► [2] Imports: os, pandas, matplotlib, sklearn.train_test_split
  │
  ├─► [3-4] Configuration: DATA_ROOT, TRAIN_DIR, TEST_DIR
  │
  ├─► [5-6] Construction df_train (exploration des données)
  │
  ├─► [7-8] Analyse des propriétés des images
  │
  ├─► [9-10] Visualisation d'exemples d'images
  │
  └─► [11-14] Analyse de la distribution des classes
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│  PARTIE 2: PRÉPARATION DES DONNÉES (Cellules 15-17)                │
└─────────────────────────────────────────────────────────────────────┘
  │
  ├─► [15] Markdown: Préparation du Split Train/Validation
  │
  ├─► [16] Code: Création de X_train, X_val, y_train, y_val
  │           avec train_test_split stratifié
  │
  └─► [17] Markdown: Section "Modélisation OCR et Classification"
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│  PARTIE 3: MODÉLISATION PYTORCH (Cellules 18-30)                   │
└─────────────────────────────────────────────────────────────────────┘
  │
  ├─► [18] Installation des packages PyTorch
  │
  ├─► [19] Imports PyTorch + Définition:
  │         - class DocumentDataset(Dataset)
  │         - train_transform
  │         - val_transform
  │
  ├─► [20-22] Définition:
  │           - class FraudDetectionModel(nn.Module)
  │
  ├─► [23-24] Définition:
  │           - def train_model(...)
  │
  ├─► [25-26] Création des objets:
  │           - train_dataset = DocumentDataset(X_train, ...)
  │           - val_dataset = DocumentDataset(X_val, ...)
  │           - train_loader = DataLoader(...)
  │           - val_loader = DataLoader(...)
  │
  ├─► [27-28] Configuration de l'entraînement:
  │           - device = torch.device(...)
  │           - model = FraudDetectionModel(...)
  │           - criterion = nn.CrossEntropyLoss(...)
  │           - optimizer = optim.Adam(...)
  │           - scheduler = ...
  │
  └─► [29-30] Lancement de l'entraînement:
              - trained_model, history = train_model(...)
              - torch.save(model.state_dict(), 'model.pth')
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│  PARTIE 4: PRÉDICTION & SOUMISSION (Cellules 31-37)                │
└─────────────────────────────────────────────────────────────────────┘
  │
  ├─► [31] Markdown: Section "Extraction OCR et Prédiction"
  │
  ├─► [32-33] Configuration des outils OCR (EasyOCR)
  │
  ├─► [34-35] Définition du pipeline de prédiction:
  │           - def predict_document(...)
  │
  └─► [36-37] Prédiction sur le test set:
              - Création de test_df
              - Création de test_dataset et test_loader
              - Boucle de prédiction: predictions = []
              - Génération de submission.csv
       │
       ▼
┌─────────────────────────────────────────────────────────────────────┐
│  ANNEXE: ANALYSE GT OCR (Cellules 38-40) - OPTIONNEL               │
└─────────────────────────────────────────────────────────────────────┘
  │
  └─► [38-40] Analyse des fichiers Ground Truth
              (non nécessaire pour le pipeline principal)

═══════════════════════════════════════════════════════════════════════

                       ✅ FIN DE L'EXÉCUTION
              Fichier submission.csv généré avec succès!
```

## Points Clés du Flux d'Exécution

### Ordre Logique Respecté

1. **Imports d'abord** ✅
   - Bibliothèques standard (cellule 2)
   - sklearn pour train_test_split (cellule 2)
   - PyTorch (cellule 19)

2. **Configuration ensuite** ✅
   - Chemins des données (cellule 4)
   - Variables d'environnement

3. **Chargement des données** ✅
   - Construction de df_train (cellule 6)
   - Exploration et visualisation (cellules 8-14)

4. **Préparation ML** ✅
   - Split train/val (cellule 16)
   - Définitions des classes (cellules 19-24)

5. **Entraînement** ✅
   - Création des datasets/loaders (cellules 26)
   - Configuration (cellule 28)
   - Entraînement (cellule 30)

6. **Prédiction et Soumission** ✅
   - Préparation du test set (cellule 37)
   - Génération submission.csv (cellule 37)

### Dépendances Résolues

| Item               | Défini en | Utilisé en | Status |
|--------------------|-----------|------------|--------|
| train_test_split   | Cell 2    | Cell 16    | ✅     |
| df_train           | Cell 6    | Cell 8+    | ✅     |
| X_train, y_train   | Cell 16   | Cell 27    | ✅     |
| DocumentDataset    | Cell 19   | Cell 26    | ✅     |
| train_transform    | Cell 19   | Cell 26    | ✅     |
| FraudDetectionModel| Cell 22   | Cell 28    | ✅     |
| train_model        | Cell 24   | Cell 30    | ✅     |
| train_loader       | Cell 26   | Cell 30    | ✅     |
| model              | Cell 28   | Cell 30    | ✅     |
