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
Para saber que estamos dentro del entorno virtual creado veremos a la izquierda de la linea actual <(cv)>.
Permanecemos centro del entorno virtual.
```
pip install numpy
```
Para salir del entorno virtual
```
deactivate
```
# 5. Instalar prerrequisitos de Opencv usando Homebrew
Fuera del entorno virtual
```
brew install cmake pkg-config
brew install jpeg libpng libtiff openexr
brew install eigen tbb
```
# 6. Descargar Opencv
```
cd ~
git clone https://github.com/opencv/opencv
git clone https://github.com/opencv/opencv_contrib
```
# 7. Configurar Opencv y Python mediante CMake
```
cd ~/opencv
mkdir build
cd build
```
Configurar el CMake. La configuracion de mi CMake segun mis rutas:
```
```
# 8. Compilar e instalar Opencv
```
make -j4
sudo make install
```
