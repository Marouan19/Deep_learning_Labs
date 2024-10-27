# Analyse Prédictive de la Consommation Énergétique à l'aide de Réseaux de Neurones LSTM

## Description du Projet
Ce projet utilise des réseaux de neurones récurrents de type LSTM (Long Short-Term Memory) pour prédire la consommation énergétique future basée sur les données historiques. L'objectif est de fournir des prévisions précises permettant une meilleure gestion et optimisation des ressources énergétiques.

## Table des Matières
1. [Prérequis](#prérequis)
2. [Installation](#installation)
3. [Structure du Projet](#structure-du-projet)
4. [Utilisation](#utilisation)
5. [Méthodologie](#méthodologie)
6. [Résultats](#résultats)
7. [Conclusion](#conclusion)

## Prérequis
- Python 3.8+
- TensorFlow 2.x
- Numpy
- Pandas
- Matplotlib
- Scikit-learn

## Installation
```bash
# Cloner le repository
git clone https://github.com/username/energy-prediction-lstm.git

# Installer les dépendances
pip install -r requirements.txt
```

## Structure du Projet
```
energy-prediction-lstm/
│
├── data/
│   ├── raw/                 # Données brutes
│   └── processed/           # Données prétraitées
│
├── models/                  # Modèles entraînés
│
├── src/
│   ├── data_processing.py   # Prétraitement des données
│   ├── model.py            # Architecture du modèle LSTM
│   └── train.py            # Script d'entraînement
│
├── notebooks/              # Notebooks Jupyter d'analyse
│
├── requirements.txt        # Dépendances du projet
└── README.md
```

## Utilisation

### Préparation des données
```python
# Exemple de préparation des données
python src/data_processing.py --input data/raw/energy_data.csv --output data/processed/
```

### Entraînement du modèle
```python
python src/train.py --data data/processed/prepared_data.csv --epochs 30 --batch_size 32
```

## Méthodologie

### Prétraitement des Données
- Normalisation des données
- Création de séquences temporelles (time steps = 7)
- Division train/test (80/20)

### Architecture du Modèle
```python
model = Sequential([
    LSTM(100, input_shape=(time_steps, 1)),
    Dense(1)
])
```

### Paramètres d'Entraînement
- Optimizer: Adam
- Loss: Mean Squared Error
- Métrique: Mean Absolute Error
- Epochs: 30
- Batch Size: 32

## Résultats

### Performances du Modèle
- Loss finale: ~0.0045
- MAE finale: ~0.053
- Validation Loss: ~0.0044
- Validation MAE: ~0.0541

### Analyse des Time Steps
Tests effectués avec différentes fenêtres temporelles :
- 7 time steps : Meilleure performance et stabilité
- 10 time steps : Performance similaire mais plus variable
- 12 time steps : Plus instable et complexe

## Conclusion
Le modèle avec 7 time steps offre le meilleur compromis entre :
- Performance prédictive
- Stabilité
- Efficacité computationnelle
- Simplicité d'implémentation

## Contributions
Les contributions sont les bienvenues ! N'hésitez pas à :
1. Fork le projet
2. Créer une branche (`git checkout -b feature/AmazingFeature`)
3. Commit vos changements (`git commit -m 'Add AmazingFeature'`)
4. Push sur la branche (`git push origin feature/AmazingFeature`)
5. Ouvrir une Pull Request

## Licence
Ce projet est sous licence MIT - voir le fichier [LICENSE](LICENSE) pour plus de détails.

## Contact
Votre Nom - [@twitter_handle](https://twitter.com/twitter_handle)
Email - votre.email@example.com
