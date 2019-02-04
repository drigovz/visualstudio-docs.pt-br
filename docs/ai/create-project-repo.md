---
title: Clonar um repositório
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.service: multiple
ms.workload:
- multiple
ms.openlocfilehash: fd0c71e9f426c5591f9ac3ecd135c1b230ca5e20
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986053"
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Clonar um repositório de código Python no Visual Studio

Depois de [instalar o suporte às Ferramentas do Visual Studio para IA](installation.md), será possível clonar facilmente um repositório de código Python e criar um projeto com base nele.

1. Para conectar-se aos repositórios do GitHub, execute o instalador do Visual Studio, selecione **Modificar** e escolha a guia **Componentes individuais**. Role para baixo até a seção **Ferramentas de código**, selecione **Extensão GitHub para Visual Studio** e escolha **Modificar**.

    ![Selecionando a extensão GitHub no instalador do Visual Studio](media/create-project-repo/installation-github-extension.png)

2. Inicie o Visual Studio.

3. Selecione **Exibir > Team Explorer** para abrir a janela do **Team Explorer**, em que é possível se conectar ao GitHub ou ao Azure DevOps ou clonar um repositório.

    ![Janela do Team Explorer mostrando o Azure DevOps, o GitHub e a clonagem de um repositório](media/create-project-repo/team-explorer-devops.png)

4. No campo de URL em **Repositórios Git Locais**, insira `https://github.com/Microsoft/samples-for-ai`, insira uma pasta para os arquivos clonados e selecione **Clonar**.

    > [!Tip]
    > A pasta especificada no Team Explorer é a pasta específica para receber os arquivos clonados. Ao contrário do comando `git clone`, criar um clone no Team Explorer não cria automaticamente uma subpasta com o nome do repositório.

5. Quando a clonagem for concluída, clique duas vezes na pasta do repositório na parte inferior do Team Explorer, para navegar até o dashboard do repositório. Em **Soluções**, selecione **Nova**.

    ![Janela do Team Explorer, criando um novo projeto com base em um clone](media/create-project-repo/team-explorer-new-project.png)

6. Na caixa de diálogo **Novo Projeto** exibida, selecione "**Do código Python Existente**", especifique um nome para o projeto, defina **Local** como a mesma pasta que o repositório e selecione **OK**. No assistente que é exibido, selecione **Concluir**.

7. Selecione **Exibir > Gerenciador de Soluções** no menu.

8. No Gerenciador de Soluções, expanda o nó `TensorFlow Examples> MNIST`, clique com botão direito do mouse em `convolutional.py` e selecione **Definir como Arquivo de Inicialização**. Esta etapa informa ao Visual Studio qual arquivo deve ser usado ao executar o projeto.

9. Pressione **Ctrl**+**F5** ou selecione **Depurar > Iniciar Sem Depuração** para executar o programa. Se aparecer um erro, verifique novamente a configuração do diretório de trabalho na etapa anterior.

10. Quando o programa é executado com sucesso, você o verá iniciando o download do seu treinamento, testando o conjunto de dados, treinando o modelo e transmitindo sua taxa de erros. Convém que a taxa de erro diminua com o tempo

    ![Primeira saída do programa MNIST do Python](media/create-project-repo/tensorflow-mnist-running.png)

   > [!NOTE]
   > Se você estiver usando o Anaconda e receber um erro sobre numpy ausente, talvez seja necessário [alterar seu ambiente de Python para usar o Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. É possível visualizar o andamento com o TensorBoard. Clique com botão direito do mouse no seu projeto e em **Executar TensorBoard**. Em seguida, selecione o diretório os seus logs do TensorBoard de saída.

   ![executar tensorboard](media/create-project-repo/run-tensorboard.png)

12. Observe o erro diminuindo com o tempo, o que significa que a qualidade está melhorando.

   ![executar tensorboard](media/create-project-repo/tensorboard.png)
