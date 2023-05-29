# Tutorial: Instalação do ROS Noetic no Ubuntu 20

Este tutorial detalha o processo de instalação do ROS Noetic no Ubuntu 20. O ROS é uma plataforma de desenvolvimento de software amplamente utilizada para robótica e sistemas autônomos. Este tutorial instala o Ros e seus pacotes principais na versão desktop.

## Pré-requisitos

Antes de prosseguir com a instalação, verifique se o seu sistema atende aos seguintes pré-requisitos:

- Ubuntu 20 instalado e atualizado.
- Acesso à internet para baixar os pacotes necessários durante a instalação.

## Passo 1: Configuração do repositório

1. Abra um terminal no Ubuntu.
2. Adicione o repositório do ROS Noetic às fontes de software do sistema executando o seguinte comando:

   ```
   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu focal main" > /etc/apt/sources.list.d/ros-noetic.list'
   ```

3. Importe a chave do repositório usando o comando abaixo:

   ```
   curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
   ```

## Passo 2: Instalação do ROS Noetic

1. Atualize a lista de pacotes disponíveis usando o seguinte comando:

   ```
   sudo apt update
   ```

2. Instale o ROS Noetic utilizando o comando a seguir:

   ```
   sudo apt install ros-noetic-desktop-full
   ```

   Esse comando instalará o conjunto completo de pacotes do ROS Noetic, incluindo bibliotecas, ferramentas e bibliotecas de visão computacional.

3. Após a conclusão da instalação, inicialize o ambiente do ROS Noetic executando o comando:

   ```
   echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
   source ~/.bashrc
   ```
   Este comando pode ser editado com os próximos tutoriais. para modificar edite o arquivo `~/.bashrc`

## Passo 3: Configuração do ambiente

1. Verifique se a instalação foi concluída com sucesso executando o seguinte comando:

   ```
   rosversion -d
   ```

   O resultado exibirá a versão instalada do ROS (noetic).
   
2. Veja o tutorial de [como configurar o catkin.](https://github.com/felipetrentin/do_zero_ao_ROS/blob/master/rosbasics.md)

## Conclusão

Parabéns! Agora você concluiu a instalação do ROS Noetic no Ubuntu 20. Este tutorial abordou os passos essenciais para configurar o ambiente de desenvolvimento do ROS em seu sistema. Para explorar ainda mais os recursos e capacidades do ROS, recomenda-se consultar a documentação oficial do ROS e os recursos disponíveis online.

Lembre-se de que este tutorial fornece uma visão geral do processo de instalação. Dependendo das suas necessidades específicas, você pode precisar instalar pacotes adicionais ou configurar outros componentes do ROS.
