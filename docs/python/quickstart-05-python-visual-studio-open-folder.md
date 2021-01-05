---
title: Início Rápido – Abrir uma pasta de código do Python
description: Neste início rápido, você abre e executa o código Python de uma pasta sem usar um projeto do Visual Studio (apenas Visual Studio 2019).
ms.date: 03/12/2019
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
monikerRange: '>= vs-2019'
ms.openlocfilehash: d11ffcb2c43d2c519d75d43afad6383e0bfaa44a
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761271"
---
# <a name="quickstart-open-and-run-python-code-in-a-folder"></a>Início rápido: abrir e executar o código Python em uma pasta

Depois de [instalar o suporte ao Python no Visual Studio 2019](installing-python-support-in-visual-studio.md), é fácil executar o código de Python existente no Visual Studio 2019 sem criar um projeto do Visual Studio.

> [!Note]
> O Visual Studio 2017 e anteriores exigiam que você criasse um projeto do Visual Studio para executar o código Python, o que você pode fazer facilmente usando um modelo de projeto interno. Consulte [início rápido: criar um projeto Python com base em código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md)

1. Para este passo a passo, use qualquer pasta com o código do Python que desejar. Para acompanhar o exemplo mostrado aqui, clone o repositório do GitHub gregmalcolm/python_koans em seu computador usando o comando `git clone https://github.com/gregmalcolm/python_koans` em uma pasta apropriada.

1. Inicie o Visual Studio de 2019 e, na janela de início, selecione **Abrir** na parte inferior da coluna **Introdução**. Como alternativa, se você já tiver o Visual Studio em execução, selecione o comando **arquivo**  >  **abrir**  >  **pasta** em vez disso.

    ![A tela de inicialização do Visual Studio](media/quickstart-open-folder/01-open-local-folder.png)

1. Navegue até a pasta que contém o código do Python e escolha **Selecionar Pasta**. Se estiver usando o código python_koans, selecione a pasta `python3` dentro da pasta de clone.

    ![A caixa de diálogo Selecionar Pasta do comando Abrir Pasta](media/quickstart-open-folder/02-select-folder.png)

1. O Visual Studio exibe a pasta no **Gerenciador de Soluções** no que é chamado de **Exibição de Pasta**. Você pode expandir e recolher pastas usando as setas nas bordas esquerdas dos nomes de pasta:

    ![Controles para expandir e recolher pastas no Gerenciador de Soluções](media/quickstart-open-folder/03-expand-collapse-folders.png)

1. Ao abrir uma pasta do Python, o Visual Studio cria várias pastas ocultas para gerenciar as configurações relacionadas ao projeto. Para ver essas pastas (e quaisquer outros arquivos e pastas ocultos, como a pasta *.git*), selecione o botão da barra de ferramentas **Mostrar Todos os Arquivos**:

    ![Uma exibição de pastas ocultas no Gerenciador de Soluções](media/quickstart-open-folder/05-view-hidden-folders.png)

1. Para executar o código, primeiro você precisa identificar o arquivo de programa principal ou de inicialização. No exemplo mostrado aqui, o arquivo de inicialização *contemplate-koans.py*. Clique com o botão direito do mouse nesse arquivo e selecione **Definir como Arquivo de Inicialização**.

    ![Definir um item de inicialização no Gerenciador de Soluções](media/quickstart-open-folder/06-set-as-startup-item-command.png)

    > [!Important]
    > Se o item de inicialização não estiver localizado na raiz da pasta que você abriu, você também deverá adicionar uma linha para o arquivo JSON de configuração de inicialização conforme descrito na seção [Definir um diretório de trabalho](#set-a-working-directory).

1. Execute o código pressionando **Ctrl** + **F5** ou selecionando **depurar**  >  **Iniciar sem Depurar**. Você também pode selecionar o botão de barra de ferramentas que mostra o item de inicialização com o botão play, que executa o código no depurador do Visual Studio. Em todos os casos, o Visual Studio detecta que seu item de inicialização é um arquivo Python; portanto, ele executa automaticamente o código no ambiente Python padrão. (Esse ambiente é mostrado à direita do item de inicialização na barra de ferramentas).

    ![Botão da barra de ferramentas Iniciar depurador](media/quickstart-open-folder/07-start-debug-toolbar.png)

1. A saída do programa aparece em uma janela de comando separada:

    ![Janela de saída para execução de código Python](media/quickstart-open-folder/08-result-window.png)

1. Para executar o código em um ambiente diferente, selecione o ambiente do controle de lista suspensa na barra de ferramentas e inicie novamente o item de inicialização.

1. Para fechar a pasta no Visual Studio, selecione o comando **arquivo**  >  menu **fechar pasta** .

## <a name="set-a-working-directory"></a>Definir um diretório de trabalho

Por padrão, o Visual Studio executa um projeto do Python aberto como uma pasta na raiz da mesma pasta. O código em seu projeto, no entanto, pode pressupor que o Python está sendo executado em uma subpasta. Por exemplo, suponha que você abra a pasta raiz do repositório python_koans e, em seguida, defina o arquivo *python3/contemplar-koans.py* como item de inicialização. Se você executar o código, verá um erro dizendo que o arquivo *koans.txt* não foi encontrado. Esse erro ocorre porque *contemplate-koans.py* pressupõe que o Python está sendo executado na pasta *python3* em vez da raiz do repositório.

Nesses casos, você também deve adicionar uma linha ao arquivo JSON de configuração de inicialização para especificar o diretório de trabalho:

1. Clique com o botão direito do mouse no arquivo de inicialização do Python (*.py*) no **Gerenciador de Soluções** e selecione **Configurações de Depuração e de Inicialização**.

    ![Captura de tela da exibição de pasta Gerenciador de Soluções com o arquivo contemplate-koans.py selecionado e configurações de depuração e inicialização selecionadas no menu de contexto.](media/quickstart-open-folder/09-debug-launch-settings-menu-command.png)

1. Na caixa de diálogo **Selecionar depurador** que aparece, selecione **Padrão** e escolha **Selecionar**.

    ![Captura de tela da caixa de diálogo Selecionar um depurador com o depurador padrão selecionado e o botão Selecionar escolhido.](media/quickstart-open-folder/10-select-debugger.png)

    > [!Note]
    > Se você não vir o **padrão** como uma opção, certifique-se de escolher um arquivo Python *. py* ao selecionar o comando **configurações de depuração e inicialização** . O Visual Studio usa o tipo de arquivo para determinar quais opções do depurador exibir.

1. O Visual Studio abre um arquivo chamado *launch.vs.json*, que está localizado na pasta *.vs* oculta. Este arquivo descreve o contexto de depuração para o projeto. Para especificar um diretório de trabalho, adicione um valor de `"workingDirectory"`, como em `"workingDirectory": "python3"` para o exemplo de python-koans:

    ```json
    {
      "version": "0.2.1",
      "defaults": {},
      "configurations": [
        {
          "type": "python",
          "interpreter": "(default)",
          "interpreterArguments": "",
          "scriptArguments": "",
          "env": {},
          "nativeDebug": false,
          "webBrowserUrl": "",
          "project": "python3\\contemplate_koans.py",
          "name": "contemplate_koans.py",
          "workingDirectory": "python3"
        }
      ]
    }
    ```

1. Salve o arquivo e inicie o programa novamente, que agora é executado na pasta especificada.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: trabalhar com Python no Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Consulte também

- [Início Rápido: Criar um projeto do Python com base em código existente](quickstart-01-python-in-visual-studio-project-from-existing-code.md)
- [Início rápido: criar um projeto Python por meio de um repositório](quickstart-03-python-in-visual-studio-project-from-repository.md)
- [Identificar manualmente um interpretador Python existente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
