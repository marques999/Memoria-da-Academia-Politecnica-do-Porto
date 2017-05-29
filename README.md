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

As seguintes instruções ilustram todos os passos necessários para fazer *build* do código-fonte das quatro aplicações que constituem este projecto:

1. Seguir as instruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Back-End/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Back-End](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Back-End). Poderá ser necessário configurar *port forwarding* na porta 3000 se a aplicação estiver a correr num servidor remoto, ou para permitir acesso aos utilizadores que se encontrem fora da rede interna, caso esteja a correr num servidor local.

2. Seguir as instruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Website/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Website](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Website). Poderá ser necessário configurar *port forwarding* na porta 3001 se a aplicação estiver a correr num servidor remoto, ou para permitir acesso aos utilizadores que se encontrem fora da rede interna, caso esteja a correr num servidor local.

3. Através da aplicação *web* do *back-office*, gerar três *API keys* que serão utilizadas pelos dois microcontroladores e pela *control application*. Deve ser gerada uma chave de cada tipo (correspondente a um dispositivo diferente), já que na configuração mais simples existe uma projecção horizontal, uma projecção vertical e uma *control application*.

4. Seguir as instruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Mobile/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Mobile](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Mobile). No final deverá gerar um ficheiro APK para instalar numa *tablet Android*.

5. Seguir as intruções de *deployment* presentes no ficheiro [README.md](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Microcontrollers/blob/master/README.md) do repositório [Memoria-da-Academia-Politecnica-do-Porto-Microcontrollers](https://github.com/LuisMDuarte95/Memoria-da-Academia-Politecnica-do-Porto-Microcontrollers). No final deverá gerar um executável **Electron** para a plataforma ```rpi```.

### Configuração ###

Os seguintes passos (separados por aplicação) explicam como instalar a *control application* numa *tablet Android*, ligar a *control application* e os microcontroladores ao servidor *back-end*, bem como configurar uma sala virtual semelhante à que será implementada no edifício da Reitoria.

#### Microcontrollers ####

1. Transferir pasta ```release``` para uma *pen USB* ou disco externo. Ligar dispositivo de armazenamento ao *Raspberry Pi*, transferindo a pasta ```release``` para o ambiente de trabalho (*desktop*).
2. Configurar um microcontrolador do tipo "projecção vertical", alterando para ```type: table```, no ficheiro ```config/default.yaml```.
3. Configurar um microcontrolador do tipo "projecção horizontal", alterando para ```type: narrative```, no ficheiro ```config/default.yaml```.
4. Em ambos os microcontroladores, configurar localização do servidor. Alterar linha ```host: http://localhost``` no ficheiro ```config/default.yaml``` para o endereço IP ou *hostname* do servidor *back-end*. **(IMPORTANTE)** O endereço deverá começar sempre por ```http://``` ou ```https://```. Configurar também porta do servidor, alterando a linha ```port: 3000``` para a respetiva porta do servidor.
6. Em ambos os microcontroladores, introduzir a *API key* que serve de autenticação e acesso ao servidor. Alterar linha ```key: apikey``` no ficheiro ```config/default.yaml``` para a *API key* atribuída a cada um dos microcontroladores. **(IMPORTANTE)** Uma *API key* atribuída a um microcontrolador do tipo "projecção vertical" não pode ser usada num microcontrolador do tipo "projecção horizontal" e vice-versa. Devem ser geradas pelo menos duas chaves, uma para cada tipo.
7. Em ambos os microcontroladores, entrar na pasta ```release``` e executar a aplicação ```mapp```. Deverá aparecer uma janela com o logótipo da aplicação a ocupar a totalidade do ecrã.

#### Mobile ####

1. Transferir APK gerado pelo comando **npm run android:release** (que pode ser encontrado em ```platform/android/build/output.apk```) para a memória interna da *tablet* através de um cabo USB ligado ao computador. Poderá ser necessário ativar uma opção para permitir a instalação de aplicações de [fontes desconhecidas](http://www.androidpit.com.br/forum/660787/como-ativar-fontes-desconhecidas). Depois de instalada, executar aplicação **MAPP**.
2. Em alternativa, ativar "depuração USB" através das [opções de programador](http://www.androidpit.com.br/como-ativar-depuracao-usb-android), ligar a *tablet* ao computador pelo cabo USB, executar comando **ionic run android**. A aplicação será lançada automaticamente, sem intervenção do utilizador.
3. Configurar ligação ao servidor *back-end*, seguindo os passos apresentados no ecrã. Deverá introduzir as seguintes informações, pela ordem apresentada, carregando no botão **Confirmar** para prosseguir ao ecrã seguinte: endereço IP ou *hostname* do servidor, porta do servidor, *API key* atribuída à *control application*.
4. Se não for apresentada qualquer mensagem de erro na tentativa de estabelecer ligação com o servidor, a *control application* está pronta a ser utilizada. Caso contrário, deverá repetir ou rever os passos de configuração do servidor *back-end*.
