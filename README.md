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
```sudo python3 tabzilla_data_preprocessing.py --dataset_name 'openml__Amazon_employee_access__34539'```

# TabZilla Experiments
## Ejecución de modelo con hiperparámetros random
```sudo python3 tabzilla_experiment.py --experiment_config 'tabzilla_experiment_config.yml' --model_name 'KNN' --dataset_dir '/home/markov/Documents/DL_Projects/tabzilla/TabZilla/datasets/openml__iris__59'```

Respuesta:
...
Trial 30 complete
trials complete. results written to /home/markov/Documents/DL_Projects/tabzilla/TabZilla/results

## Visualizar algoritmos disponibles:
```sudo python3 tabzilla_alg_handler.py```

all algorithms:
LinearModel
KNN
SVM
DecisionTree
RandomForest
XGBoost
CatBoost
LightGBM
MLP
TabNet
VIME
TabTransformer
NODE
DeepGBM
STG
NAM
DeepFM
SAINT
DANet
TabPFNModel
rtdl_MLP
rtdl_ResNet
rtdl_FTTransformer

## Nueva configuración
Para modificar la configuración de hiperparámetros:
- Creación de un nuevo archivo .yml
```sudo touch tabzilla_experiment_myconfig.yml```

- Modificación en terminal:
```sudo nano /home/markov/Documents/DL_Projects/tabzilla/TabZilla/tabzilla_experiment_myconfig.yml```

- Nueva configuración:
###### directory where results will be written
output_dir: ./my_results/

###### experiment & trial time limit in seconds (10 hours / 2 hours)
experiment_time_limit: 36000
trial_time_limit: 3600

###### number of trials for hyperparameter search & optimization
n_random_trials: 10
n_opt_trials: 0
hparam_seed: 0

###### GPU parameters
use_gpu: True
gpu_ids: [0]
data_parallel: True

###### Training parameters
batch_size: 64
val_batch_size: 128
early_stopping_rounds: 20
epochs: 200
logging_period: 100
scale_numerical_features: Quantile

- Nueva ejecución con "myconfig.yml":
```sudo python3 tabzilla_experiment.py --experiment_config 'tabzilla_experiment_myconfig.yml' --model_name 'KNN' --dataset_dir '/home/markov/Documents/DL_Projects/tabzilla/TabZilla/datasets/openml__iris__59'```

- Elimnar carpeta nueva:
```sudo rm -r /home/markov/Documents/DL_Projects/tabzilla/TabZilla/my_results```

- Ejecuciones con otros modelos (TabTransformer):
```sudo python3 tabzilla_experiment.py --experiment_config 'tabzilla_experiment_myconfig.yml' --model_name 'TabTransformer' --dataset_dir '/home/markov/Documents/DL_Projects/tabzilla/TabZilla/datasets/openml__Amazon_employee_access__34539'```