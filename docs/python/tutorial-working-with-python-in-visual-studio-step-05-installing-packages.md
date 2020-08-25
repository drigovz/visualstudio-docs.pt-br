---
title: Etapa 5 do Tutorial do Python no Visual Studio, pacotes de instalação
titleSuffix: ''
description: Etapa 5 de um passo a passo básico das funcionalidades do Python no Visual Studio, demonstrando os recursos do Visual Studio para gerenciar pacotes em um ambiente Python.
ms.date: 03/09/2020
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 32e85f39c4acf9466def24bcfea59bbfd6807a1b
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801653"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Etapa 5: Instalar pacotes no ambiente do Python

**Etapa anterior: [executar o código no depurador](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

A comunidade de desenvolvedores do Python produziu milhares de pacotes úteis que você pode incorporar em seus próprios projetos. O Visual Studio oferece uma interface do usuário para gerenciar pacotes em seus ambientes do Python.

## <a name="view-environments"></a>Exibir ambientes

1. Selecione o comando de menu **Exibir**  >  **outros**  >  **ambientes Python** do Windows. A janela **Ambientes de Python** será aberta como um par com o **Gerenciador de Soluções** e mostrará os diferentes ambientes disponíveis para você. A lista mostra os ambientes que você instalou usando o instalador do Visual Studio e os que você instalou separadamente. Isso inclui ambientes globais, virtuais e Conda. O ambiente em negrito é o ambiente padrão, que é usado para novos projetos. Para obter informações adicionais sobre como trabalhar com ambientes, consulte [como criar e gerenciar ambientes Python em ambientes do Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Janela Ambientes do Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Você também pode abrir a janela ambientes Python selecionando a janela Gerenciador de Soluções e usando o atalho de teclado **Ctrl + K, CTRL + '** . Se o atalho não funcionar e você não conseguir encontrar a janela ambientes Python no menu, é possível que você não tenha instalado a carga de trabalho do Python. Consulte [como instalar o suporte do Python no Visual Studio](installing-python-support-in-visual-studio.md) para obter orientação sobre como instalar o Python.

2. A guia **visão geral** do ambiente fornece acesso rápido a uma janela **interativa** para esse ambiente, juntamente com a pasta de instalação e os intérpretes do ambiente. Por exemplo, selecione **Abrir janela interativa** e uma janela **interativa** para esse ambiente específico aparece no Visual Studio.

3. Agora, crie um novo projeto com **arquivo**  >  **novo**  >  **projeto**, selecionando o modelo de **aplicativo Python** . No arquivo de código que aparece, Cole o código a seguir, que cria uma onda do cosseno como as etapas anteriores do tutorial, apenas neste momento plotado graficamente. Como alternativa, você pode usar o projeto criado anteriormente e substituir o código.

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

4. Com um projeto Python aberto, você também pode abrir a janela ambientes Python de Gerenciador de Soluções clicando com o botão direito do mouse em **ambientes Python** e selecionando **Exibir todos os ambientes de Python**

   ![Ambiente](media/environments/environments-view-all-2019.png)

5. Observando a janela do editor, você observará que, se você passar o mouse sobre as `numpy` `matplotlib` instruções e importar, elas não serão resolvidas. Isso ocorre porque os pacotes não foram instalados no ambiente global padrão.

   ![Importação de pacote não resolvido](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instalar pacotes usando a janela ambientes Python

1. Na janela ambientes do Python, selecione o ambiente padrão para novos projetos do Python e escolha a guia **pacotes** . Em seguida, você verá uma lista de pacotes que estão atualmente instalados no ambiente.

   ![Pacotes instalados em um ambiente](media/environments/environments-installed-packages-2019.png)

2. Instale o `matplotlib` inserindo seu nome no campo de pesquisa e, em seguida, selecionando a opção **executar comando: Pip install matplotlib** . Isso será instalado `matplotlib` , bem como quaisquer pacotes dos quais depende (nesse caso, inclui `numpy` ).

   ![Instalação do matplotlib no ambiente](media/environments/environments-add-matplotlib-2019.png)

5. Dê permissão para a elevação, se for solicitado.

6. Depois que o pacote é instalado, ele aparece na janela **ambientes Python** . O **X** à direita do pacote serve para desinstalá-lo.

   ![Conclusão da instalação do matplotlib no ambiente](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Uma pequena barra de progresso pode aparecer embaixo do ambiente para indicar que o Visual Studio está criando seu banco de dados IntelliSense para o pacote recém-instalado. A guia **IntelliSense** também mostra mais informações detalhadas. Lembre-se de que até que esse banco de dados seja concluído, os recursos do IntelliSense, como a conclusão automática e a verificação de sintaxe, não estarão ativos no editor desse pacote.
   >
   > O Visual Studio 2017 versão 15,6 e posterior usa um método diferente e mais rápido para trabalhar com o IntelliSense e exibe uma mensagem para esse efeito na guia **IntelliSense** .

## <a name="run-the-program"></a>Executar o programa

1. Agora que o [matplotlib](https://matplotlib.org/) está instalado, execute o programa com (**F5**) ou sem o depurador (**Ctrl** + **F5**) para ver a saída:

   ![Saída de exemplo de matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Trabalhar com o Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Aprofunde-se um pouco mais

- [Ambientes do Python](managing-python-environments-in-visual-studio.md)
- [Saiba mais sobre Django no Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Conheça o Flask no Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
