# O que é um Workspace?

Um workspace do ROS (Robot Operating System) é um diretório especial usado para organizar e gerenciar os pacotes de software relacionados a um projeto de robótica ou sistema autônomo. É dentro do workspace que você desenvolve e constrói seus pacotes do ROS, que podem incluir bibliotecas, drivers, aplicativos e outros componentes.

O uso de workspaces do ROS facilita o gerenciamento de dependências entre os pacotes, permitindo que você trabalhe em projetos complexos com vários componentes interconectados.

# Criando um Workspace no **ROS**

Existe mais de uma maneira de criar um Workspace no ROS. Para este projeto, vamos utilizar o *catkin tools* por sua simplicidade e uso bem difundido.

Para instalar veja o tutorial [aqui.](https://catkin-tools.readthedocs.io/en/latest/installing.html) Recomandamos intalar pelo apt-get ou source, pois pip é o mais lento.

É importante notar que o Catkin Tools substitui o antigo sistema de construção rosmake, oferecendo uma abordagem mais moderna e flexível para desenvolvimento com o ROS.

catkin tools trabalha com um comando principal `catkin` e diversos argumentos.

**Um repositório criado no catkin tools não deve ser utilizado com catkin e rosmake ou vice-versa.**

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
    Cada pacote é geralmente colocado em seu próprio subdiretório dentro de src, ou seja, cada pasta nesse diretório pode conter um ou mais pacotes.
2. ## build
    será a pasta em que CMake é chamado para compilar os pacotes da pasta src. CMake e katkin deixam seus arquivos intermediários e artefatos gerados durante o processo de compilação aqui.
3. ## devel
    Após a compilação bem-sucedida dos pacotes do ROS, os arquivos resultantes são instalados no diretório devel. Esse diretório contém os executáveis, bibliotecas e outros recursos gerados pelos pacotes do ROS. Estes arquivos estão na estrutura de intalação antes de serem instalados, para realizar a tarefa de testes sem chamar a instrução de instalação.
    além disso, é necessário rodar em todos terminais abertos o comando
    ```source devel/setup.bash``` para ativar o Workspace. Portanto este comando comunmente é encontrado no final de `~/.bashrc`
4. ## logs
    armazena todos os logs de compilação e execução.
5. install: 
    Em vez de usar o diretório devel, você também pode optar por instalar seus pacotes do ROS no diretório install. Isso permite que você mantenha um ambiente de compilação limpo separado do ambiente de execução.

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

## Criando um novo pacote

Agora que o workspace do Catkin está configurado, você pode criar um novo pacote no ROS. Siga as etapas abaixo:

1. No diretório `src`, execute o seguinte comando para criar um novo pacote chamado `my_package`:

   ```
   catkin create pkg my_package
   ```

2. O Catkin Tools irá criar a estrutura básica do pacote `my_package` com os arquivos necessários. Agora, você pode personalizar o pacote adicionando seus próprios arquivos e código-fonte.

## Compilamdo o pacote

Após criar o pacote, é necessário compilá-lo antes de usá-lo. Siga as etapas abaixo:

1. Navegue até o diretório raiz do workspace do Catkin:

   ```
   cd ~/catkin_ws
   ```

2. Execute o comando `catkin build` para compilar todos os pacotes no workspace:

   ```
   catkin build
   ```

3. O Catkin Tools irá compilar o pacote `my_package` e suas dependências. Verifique se a compilação foi bem-sucedida e se não houve erros.


Lembre-se de que este tutorial abrange apenas os passos básicos para criar um pacote usando o Catkin Tools. Existem várias opções e recursos adicionais disponíveis para personalizar e configurar seus pacotes. Consulte a documentação oficial do ROS e a documentação do Catkin Tools para obter mais informações e explorar recursos avançados.
