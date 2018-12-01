# Instalacion_OpenCV_Mac
# 1. Instalar Xcode
```
sudo xcodebuild -license
sudo xcode-select --install
```
# 2. Install Homebrew
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew update
nano ~/.bash_profile
```
Añadir al final del archivo
```
# Homebrew
export PATH=/usr/local/bin:$PATH
```
Cerrar el editor nano
```
source ~/.bash_profile
```
# 3. Configurar Hombebrew
```
brew install python3
```
Para corroborar que la instalacion es correcta, se busca que python se está usando y tendria que devolver la ruta: /usr/local/bin/python3
```
which python3
```
# 4. Instalar el entorno virtual de Python y numpy 
```
pip3 install virtualenv virtualenvwrapper
nano ~/.bash_profile
```
Añadir al final del archivo
```
# Virtualenv/VirtualenvWrapper
source /usr/local/bin/virtualenvwrapper.sh
```
Cerrar el editor nano
```
source ~/.bash_profile
```
Crear el entorno virtual para Python 3
```
mkvirtualenv cv -p python3
workon cv
```
