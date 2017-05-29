<img src="docs/logo_mapp1.png" alt="Logótipo MAPP" width="400px"/>

# Memória da Academia Politécnica do Porto #
## In Hand ##

# Índice #

1. [Apresentação](#apresentação)
2. [Deployment](#deployment)
3. [Configuração](#configuração)

### Apresentação ###

O projeto consiste na criação de um espaço de memória para a Academia Politécnica do Porto onde os visitantes poderão viajar no tempo através de uma experiência inovadora que irá contar diferentes histórias acerca do edifício da Reitoria e dos seus arredores ao longo dos anos. É um produto maioritariamente constituído por duas grandes componentes, *software* e multimédia que se interligam e que se complementam, garantindo aos utilizadores uma experiência única.

Através de uma aplicação *mobile*, cada visitante poderá selecionar diferentes narrativas e visualizá-las quer sob formato de uma projeção do edifício numa maqueta, quer sob a visualização de conteúdos multimédia projetados numa parede. Estes conteúdos serão carregados de forma dinâmica para uma plataforma web de intuitivo acesso e utilização para os administradores do sistema.

### Deployment ###

_The following steps should explain what is needed to build the
source code provided for PRODUCTION and be simple enough for even a non-tech
person to successfully do all the steps without any external help.
However, if an expert or external help is required, you should indicate it_

1. Seguir as instruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Back-End/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Back-End](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Back-End). Poderá ser necessário configurar *port forwarding* na porta 3000 se a aplicação estiver a correr num servidor remoto, ou para permitir acesso aos utilizadores que se encontrem fora da rede interna, caso esteja a correr num servidor local.

2. Seguir as instruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Website/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Website](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Website). Poderá ser necessário configurar *port forwarding* na porta 3001 se a aplicação estiver a correr num servidor remoto, ou para permitir acesso aos utilizadores que se encontrem fora da rede interna, caso esteja a correr num servidor local.

3. Seguir as instruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Mobile/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Mobile](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Mobile).

4. Seguir as intruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Microcontrollers/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Microcontrollers](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Microcontrollers).

### Configuração ###

_If the project is already generated,
then describe what the user has to do to run it.
Describe it in the most simple and clear way through ordered steps._

#### Microcontrollers ####

1. Transferir pasta ```release``` para uma *pen USB* ou disco externo. Ligar dispositivo de armazenamento ao *Raspberry Pi*, transferindo a pasta ```release``` para o ambiente de trabalho (*desktop*).
2. Em alternativa, ligar cartão SD do *Raspberry Pi* ao computador, copiando a pasta ```release``` para a localização ```/home/mapp/Desktop```. 
3. Configurar um microcontrolador do tipo "projecção vertical", alterando para ```type: table```, no ficheiro ```config/default.yaml```.
4. Configurar um microcontrolador do tipo "projecção horizontal", alterando para ```type: narrative```, no ficheiro ```config/default.yaml```.
5. Em ambos os microcontroladores, configurar localização do servidor. Alterar linha ```host: http://localhost``` para o endereço IP ou *hostname* do servidor *back-end*. **(IMPORTANTE)** O endereço deverá começar sempre por ```http://``` ou ```https://```
6. Em ambos os microcontroladores, configurar porta do servidor. Alterar linha ```port: 3000``` para a respetiva porta do servidor *back-end*.

#### Mobile ####

1. Transferir APK gerado pelo comando **npm run android:release** (que pode ser encontrado em ```platform/android/build/output.apk```) para a memória interna da *tablet* através de um cabo USB ligado ao computador. Poderá ser necessário ativar uma opção para permitir a instalação de aplicações de [fontes desconhecidas](http://www.androidpit.com.br/forum/660787/como-ativar-fontes-desconhecidas). Depois de instalada, executar aplicação **MAPP**.
2. Em alternativa, ativar "depuração USB" através das [opções de programador](http://www.androidpit.com.br/como-ativar-depuracao-usb-android), ligar a *tablet* ao computador pelo cabo USB, executar comando **ionic run android**. A aplicação será lançada automaticamente, sem intervenção do utilizador.
3. Configurar ligação ao servidor *back-end*, seguindo os passos apresentados no ecrã. Deverá introduzir as seguintes informações, pela ordem apresentada: endereço IP ou *hostname* do servidor, porta do servidor, *API key* atribuída à *control application*.
4. Se não for apresentada nenhuma mensagem de erro na tentativa de estabelecer ligação com o servidor, a *control application* está pronta a ser utilizada. Caso contrário, deverá repetir ou rever os passos de configuração do servidor *back-end*.
