---
title: Início Rápido – Criar um projeto do Python usando em modelo
description: Neste início rápido, crie um projeto do Visual Studio para Python usando um modelo interno para compilar um aplicativo básico em Flask.
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 81f337cf3feca517f46632e7fe08a9f5a62cd707
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902454"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Início Rápido: criar um projeto do Python com base em um modelo no Visual Studio

Depois de [instalar o suporte ao Python no Visual Studio](installing-python-support-in-visual-studio.md), é fácil criar um projeto do Python usando uma variedade de modelos. Neste Início Rápido, crie um aplicativo simples em Flask usando um modelo. O projeto resultante é semelhante ao projeto que você cria manualmente em [Início Rápido: criar um aplicativo Web com o Flask](../ide/quickstart-python.md).

1. Inicie o Visual Studio.

1. Na barra de menus superior, escolha **arquivo**  >  **novo**  >  **projeto** e, na caixa de diálogo **novo projeto** , procure "Flask em branco", selecione o modelo de **projeto Web Flask em branco** na lista intermediária, dê um nome ao projeto e selecione **OK**:

    ![Criar um novo projeto com o modelo de Projeto Web Flask em branco](media/quickstart-python-06-blank-flask-template.png)

1. O Visual Studio solicita a você uma caixa de diálogo que diz que **este projeto requer pacotes externos.** Essa caixa de diálogo aparece porque o modelo inclui um arquivo *requirements.txt* que especifica uma dependência do Flask. O Visual Studio pode instalar os pacotes automaticamente e oferece a opção de instalá-los em um *ambiente virtual*. É recomendável usar um ambiente virtual na instalação em um ambiente global, portanto, selecione **Instalar em um ambiente virtual** para continuar.

    ![Instalar o Flask em um ambiente virtual](media/quickstart-python-07-install-into-virtual-environment.png)

1. O Visual Studio exibe a caixa de diálogo **Adicionar Ambiente Virtual**. Aceite o padrão e selecione **Criar**, depois aprove todas as solicitações de elevação.

    > [!Tip]
    > Quando você inicia um projeto, é altamente recomendável criar um ambiente virtual imediatamente, como a maioria dos modelos do Visual Studio solicita. Ambientes virtuais mantêm os requisitos exatos do projeto ao longo do tempo, conforme você adiciona e remove bibliotecas. É possível gerar facilmente um arquivo *requirements.txt*, que você usa para reinstalar essas dependências em outros computadores de desenvolvimento (como quando usar controle do código-fonte) e ao implantar o projeto em um servidor de produção. Para saber mais sobre ambientes virtuais e seus benefícios, veja [Usar ambientes virtuais](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments) e [Gerenciar os pacotes necessários com requirements.txt](../python/managing-required-packages-with-requirements-txt.md).

1. Depois que o Visual Studio criar esse ambiente, examine o **Gerenciador de Soluções** para ver se há um arquivo *app.py* junto com *requirements.txt*. Abra *app.py* para ver se o modelo forneceu um código como em [Início Rápido: criar um aplicativo Web com o Flask](../ide/quickstart-python.md), com algumas seções adicionadas. Todo o código mostrado abaixo é criado pelo modelo, portanto você não precisa colar nada no *app.py* por conta própria.

    O código começa com as importações necessárias:

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    Em seguida está a linha seguinte que pode ser útil ao implantar um aplicativo em um host da Web:

    ```python
    wsgi_app = app.wsgi_app
    ```

    Depois, vem o decorador de rota em uma função simples que define uma exibição:

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    Por fim, o código de inicialização abaixo permite que você defina o host e a porta por meio de variáveis de ambiente em vez de fazer o hard-coding deles. Esse código permite controlar facilmente a configuração nos computadores de desenvolvimento e produção sem alterar o código:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Selecione **depurar**  >  **Iniciar sem depuração** para executar o aplicativo e abrir um navegador para `localhost:5555` .

**Pergunta: Quais outros modelos de Python o Visual Studio oferece?**

**Resposta**: Com a carga de trabalho de Python instalada, o Visual Studio fornece uma variedade de modelos de projeto, inclusive para as [estruturas da Web Flask, Bottle e Django](../python/python-web-application-project-templates.md), serviços de nuvem do Azure, diferentes cenários de aprendizado de máquina e até mesmo um modelo para criar um projeto a partir de uma estrutura de pasta existente que contenha um aplicativo do Python. Acesse-os por meio da caixa de diálogo **arquivo**  >  **novo**  >  **projeto** selecionando o nó de linguagem **Python** e seus nós filho.

O Visual Studio também fornece uma variedade de modelos de arquivo ou *Item* para criar rapidamente uma classe Python, um pacote Python, um teste de unidade do Python, arquivos de *web.config* e muito mais. Quando você tiver um projeto do Python aberto, acesse os modelos de item por meio do  >  comando do menu **Adicionar novo item** do projeto. Consulte a referência de [modelos de item](python-item-templates.md).

O uso de modelos pode economizar um tempo significativo ao iniciar um projeto ou criar um arquivo, além de ser uma ótima maneira de aprender sobre os diferentes tipos de aplicativo e estruturas de código. É útil levar reservar alguns minutos para criar projetos e itens a partir de vários modelos para se familiarizar com o que eles oferecem.

**Pergunta: Também é possível usar modelos do Cookiecutter?**

**Resposta**: Sim! Na verdade, o Visual Studio fornece integração direta com o CookieCutter, que você pode aprender sobre por meio [do início rápido: criar um projeto de um modelo de CookieCutter](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Tutorial: trabalhar com Python no Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Confira também

- [Identificar manualmente um interpretador Python existente](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Instalar o suporte para Python no Visual Studio 2015 e anterior](installing-python-support-in-visual-studio.md)
- [Locais de instalação](installing-python-support-in-visual-studio.md#install-locations)
