# O que é um Workspace?

# Criando um Workspace no **ROS**

Existe mais de uma maneira de criar um Workspace no ROS. Para este projeto, vamos utilizar o *catkin tools* por sua simplicidade e uso bem difundido.

Para instalar veja o tutorial [aqui.](https://catkin-tools.readthedocs.io/en/latest/installing.html) Recomandamos intalar pelo apt-get ou source, pois pip é o mais lento.

catkin tools trabalha com um comando principal `catkin` e diversos argumentos.

**Um repositório criado no catkin tools não deve ser utilizado com catkin ou vice-versa.**

Para criar o Workspace vá para o diretório em que você deseja criar.
(geralmente o mesmo de `echo $HOME`)

crie um diretório com o nome do seu workspace (exemplo vsssWS)
```
mkdir vsssWS
```
inicie seu workspace:
```
cd vsssWS
catkin init 
```
neste momento o catkin vai criar a pasta oculta `.catkin_tools` onde serão armazenadas todas as configurações.

crie as pastas build, devel, logs e src

(apenas a pasta src é obrigatória, porém isso facilita ao desenvolver antes de compilar.)

```
mkdir src
mkdir build
mkdir devel
mkdir logs
```
## funcões das pastas:
1. ## src
    será a pasta em que serão colocados todos os [pacotes]() do ROS em catkin (ex. realsense-ros)
    pode ser colocado um `CMakeLists.txt` como um arquivo CMake de alto nível.
    cada pasta nesse diretório pode conter um ou mais pacotes.
2. ## build
    será a pasta em que CMake é chamado para compilar os pacotes da pasta src. CMake e katkin deixam seus arquivos intermediários aqui.
3. ## devel
    pasta de desenvolvimento, em que os arquivos são colocados antes de serem instalados, para realizar a tarefa de testes sem chamar a instrição de instalação já que estão organizados da mesma maneira de quando instalados.
    além disso, é necessário rodar em todos terminais abertos o comando
    ```source devel/setup.bash``` para ativar o Workspace. Portanto este comando comunmente é encontrado no final de `~/.bashrc`
4. ## logs
    armazena todos os logs de compilação e execução.

para utilizar nosso workspace, vamos editar o `~/.bashrc`
```
nano ~/.bashrc
```
vá até o final do arquivo e adicione (caso necessário mude noetic para sua distribuição de ROS)
### OBS: mude os caminhos de acordo com sua configuração!
```
source /opt/ros/noetic/setup.bash # ativar o ROS
source /usr/share/gazebo/setup.sh # ativar o gazebo (simulador)
source ~/vsssWS/devel/setup.bash  # ativa o workspace
export ROS_WORKSPACES="~/vsssWS"  # define workspace como workspace do ROS
```
## **Pronto!**
não esqueça de salvar e sair. Seu workspace estará disponível após fechar o terminal e abrir novamente (ou executando `source ~\.bashrc`)

é comum a pasta devel estar vazia. Não se preocupe, o erro vai desaparecer após compilar o workspace.
# criando um pacote
```
catkin create pkg meu-primeiro-pacote
```
# compilando um pacote
```
catkin build
```