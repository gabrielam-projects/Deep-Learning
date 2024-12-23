# Deep-Learning

# Inicio de proyecto: 
## 1. Clonar repositorio
sudo git clone https://github.com/naszilla/tabzilla

## 2. Creación y activación de entorno virtual
python3.10 --version
python3.10 -m venv ./env_tabzilla
source /home/markov/Documents/DL_Projects/env_tabzilla/bin/activate

## 3. Instalación de requerimientos
cd tabzilla/Tabzilla
pip install -r ./pip_requirements.txt

## 4. Instalación de paquetes manuales
pip install optuna scikit-learn openml configargparse

# Ejecución de pruebas según documentación
## Activación de permisos
sudo chmod +w ./unittests

# Ejecución de test:
sudo python3 -m unittest unittests.test_experiments