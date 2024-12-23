# Deep-Learning: Tabzilla notes

# Inicio de proyecto: 
## 1. Clonar repositorio
```sudo git clone https://github.com/naszilla/tabzilla```

## 2. Creación y activación de entorno virtual
```python3.10 --version```
```python3.10 -m venv ./env_tabzilla```
```source /home/markov/Documents/DL_Projects/env_tabzilla/bin/activate```

## 3. Instalación de requerimientos
```cd tabzilla/Tabzilla```
```pip install -r ./pip_requirements.txt```

## 4. Instalación de paquetes manuales
```pip install optuna scikit-learn openml configargparse```

# Pruebas según documentación
## Activación de permisos
```sudo chmod +w ./unittests```

## Ejecución de test unitario:
```sudo python3 -m unittest unittests.test_experiments```

Respuesta:
Ran 2 tests in 28.959s

OK

## Ejecución de algoritmos


# Conversión de datasets
## Visualización de datasets disponibles en openml
```python3 tabzilla_data_preprocessing.py --print_dataset_names```

## Conversión de dataset a formato .npy.gz
```sudo python3 tabzilla_data_preprocessing.py --dataset_name 'openml__iris__59'```

# TabZilla Experiments
## Ejecución de modelo con hiperparámetros random
```sudo python3 tabzilla_experiment.py --experiment_config 'tabzilla_experiment_config.yml' --model_name 'KNN' --dataset_dir '/home/markov/Documents/DL_Projects/tabzilla/TabZilla/datasets/openml__iris__59'```

Respuesta:
...
Trial 30 complete
trials complete. results written to /home/markov/Documents/DL_Projects/tabzilla/TabZilla/results