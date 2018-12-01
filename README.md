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
workon cv
```
Configurar el CMake. La configuracion de mi CMake segun mis rutas:
```
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
    -D PYTHON3_LIBRARY=/usr/local/Cellar/python/3.7.1/Frameworks/Python.framework/Versions/3.7/lib/python3.7/config-3.7m-darwin/libpython3.7.dylib \
    -D PYTHON3_INCLUDE_DIR=/usr/local/Cellar/python/3.7.1/Frameworks/Python.framework/Versions/3.7/include/python3.7m/ \
    -D PYTHON3_EXECUTABLE=/Users/lordlobete/.virtualenvs/cv/bin/python3  \
    -D BUILD_opencv_python2=OFF \
    -D BUILD_opencv_python3=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=ON \
    -D BUILD_EXAMPLES=ON ..
```
# 8. Compilar e instalar Opencv
```
workon cv
make -j4
sudo make install
```
# 9.Renombrar y crear enlace simbólico a Opencv y python
```
deactivate
cd /usr/local/python/cv2/python-3.7
sudo mv cv2.cpython-37m-darwin.so cv2.so
cd .virtualenvs/cv/lib/python3.7/site-packages/
ln -s /usr/local/python/cv2/python-3.7/cv2.so cv2.so
```
# 10. Verificar la version de Opencv
```
workon cv
python
import cv2
cv2.__version__
deactivate
```
