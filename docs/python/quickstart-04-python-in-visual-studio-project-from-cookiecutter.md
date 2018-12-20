---
title: Início Rápido – Criar um projeto Python usando o Cookiecutter
description: Neste início rápido, crie um projeto do Visual Studio para Python usando um modelo do Cookiecutter.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: b8ad6d53a337e6a2a0d879ff9637156fb3d6d791
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062697"
---
# <a name="quickstart-create-a-project-from-a-cookiecutter-template"></a>Início Rápido: Criar um projeto por meio de um modelo do Cookiecutter

Depois de [instalar o suporte ao Python no Visual Studio 2017](installing-python-support-in-visual-studio.md), é fácil criar um novo projeto com base em um modelo do Cookiecutter, incluindo os vários modelos que estão publicados no GitHub. O [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/) fornece uma interface gráfica do usuário para descobrir modelos e opções de modelo de entrada e criar projetos e arquivos. Ele é incluído no Visual Studio 2017 e pode ser instalado separadamente em versões anteriores do Visual Studio.

1. Para este guia de início rápido, primeiro instale a distribuição Anaconda3 do Python, que inclui os pacotes do Python necessários para o modelo do Cookiecutter que será mostrado aqui. Execute o instalador do Visual Studio, escolha **Modificar**, expanda as opções de **Desenvolvimento do Python** no lado direito e escolha **Anaconda3** (32 bits ou 64 bits). Observe que a instalação poderá levar algum tempo, dependendo da velocidade da Internet, mas essa é a maneira mais simples de instalar os pacotes necessários.

1. Inicie o Visual Studio.

1. Escolha **Arquivo** > **Novo** > **De Cookiecutter**. Esse comando abre uma janela no Visual Studio, na qual você pode procurar modelos. 

    ![Novo projeto de modelo do Cookiecutter](media/projects-from-cookiecutter1.png)

1. Escolha o modelo **Microsoft/python-sklearn-classifier-cookiecutter** e escolha **Avançar**. (O processo poderá levar vários minutos na primeira vez que você usar Cookiecutter).

1. Na próxima etapa, defina um local para o novo projeto no campo **Criar Para** e, em seguida, selecione **Criar**.

    ![Segunda etapa usando o Cookiecutter, configurando propriedades do projeto](media/projects-from-cookiecutter2.png)

1. Quando o processo for concluído, você verá a mensagem **Arquivos criados com êxito.** Selecione o comando **Abrir no Gerenciador de Soluções** para abrir o projeto.

1. Pressione **Ctrl**+**F5** ou escolha **Depurar** > **Iniciar Sem Depuração** para executar o programa. 

    ![Saída do projeto do modelo python-sklearn-classifier-cookiecutter](media/projects-from-cookiecutter4.png)

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: Trabalhar com o Python no Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Consulte também

- [Usar a extensão Cookiecutter](using-python-cookiecutter-templates.md)
- [Identificar manualmente um interpretador Python existente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalar o suporte para Python no Visual Studio 2015 e anterior](installing-python-support-in-visual-studio.md)
- [Locais de instalação](installing-python-support-in-visual-studio.md#install-locations)
