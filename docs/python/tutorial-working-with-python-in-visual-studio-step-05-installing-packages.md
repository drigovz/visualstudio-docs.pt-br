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
ms.openlocfilehash: 5e2644ccfff0e7c653f4ce2680299aea95a55ef9
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "79372891"
---
# <a name="step-5-install-packages-in-your-python-environment"></a>Etapa 5: Instalar pacotes no ambiente do Python

**Etapa anterior: [executar o código no depurador](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

A comunidade de desenvolvedores do Python produziu milhares de pacotes úteis que você pode incorporar em seus próprios projetos. O Visual Studio oferece uma interface do usuário para gerenciar pacotes em seus ambientes do Python.

## <a name="view-environments"></a>Exibir ambientes

1. Selecione o **comando Exibir** > outros**ambientes python do** **Windows.** >  A janela **Ambientes de Python** será aberta como um par com o **Gerenciador de Soluções** e mostrará os diferentes ambientes disponíveis para você. A lista mostra os dois ambientes que você instalou usando o instalador do Visual Studio e aqueles que você instalou separadamente. Isso inclui ambientes globais, virtuais e conda. O ambiente em negrito é o ambiente padrão, que é usado para novos projetos. Para obter informações adicionais sobre como trabalhar com ambientes, consulte [Como criar e gerenciar ambientes Python em ambientes do Visual Studio](managing-python-environments-in-visual-studio.md).

   ![Janela Ambientes do Python](media/environments/environments-default-view-2019.png)

   > [!NOTE]
   > Você também pode abrir a janela Ambientes Python clicando na janela Do Solution Explorer e usando o atalho de teclado Ctrl+K, Ctrl+'. Se o atalho não funcionar e você não conseguir encontrar a janela Ambientes Python no menu, é possível que você não tenha instalado a carga de trabalho python. [Veja como instalar o suporte ao Python no Visual Studio](installing-python-support-in-visual-studio.md) para obter orientações sobre como instalar o Python.

2. A guia **Visão Geral** do ambiente fornece acesso rápido a uma janela **Interativa** para esse ambiente, juntamente com a pasta de instalação do ambiente e intérpretes. Por exemplo, selecione **Abrir janela interativa** e uma janela **Interativa** para esse ambiente específico aparece no Visual Studio.

3. Agora, crie um novo projeto com **o File** > **New** > **Project,** selecionando o modelo do Aplicativo **Python.** No arquivo de código que aparece, cole o seguinte código, que cria uma onda cossena como as etapas do tutorial anterior, só que desta vez plotado graficamente. Alternativamente, você pode usar o projeto que você criou anteriormente e substituir o código. 

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

4. Com um projeto Python aberto, você também pode abrir a janela Ambientes Python do Solution Explorer clicando com o botão direito em Ambientes Python e selecionando **Exibir todos os ambientes Python**

   ![Ambiente](media/environments/environments-view-all-2019.png)

5. Olhando para a janela do editor, você notará que se você passar o tempo sobre as `numpy` declarações de importação e `matplotlib` importar que elas não estão resolvidas. Isso porque os pacotes não foram instalados no ambiente global padrão.

   ![Importação de pacotes não resolvido](media/packages-unresolved-import.png)

## <a name="install-packages-using-the-python-environments-window"></a>Instale pacotes usando a janela Ambientes Python

1. Na janela Ambientes Python, clique no ambiente padrão para novos projetos Python e selecione a guia **Pacotes.** Em seguida, você verá uma lista de pacotes que estão atualmente instalados no ambiente.

   ![Pacotes instalados em um ambiente](media/environments/environments-installed-packages-2019.png)

2. Instale `matplotlib` inserindo seu nome no campo de pesquisa e, em seguida, selecionando o **comando Executar: pip instalar matplotlib** opção. Isso será `matplotlib`instalado, assim como quaisquer pacotes que dependam `numpy`(neste caso, que inclui ).

   ![Instalação do matplotlib no ambiente](media/environments/environments-add-matplotlib-2019.png)

5. Dê permissão para a elevação, se for solicitado.

6. Depois que o pacote é instalado, ele aparece na janela **Ambientes Python.** O **X** à direita do pacote serve para desinstalá-lo.

   ![Conclusão da instalação do matplotlib no ambiente](media/environments/environments-add-matplotlib2-2019.png)

   > [!NOTE]
   > Uma pequena barra de progresso pode aparecer embaixo do ambiente para indicar que o Visual Studio está construindo seu banco de dados IntelliSense para o pacote recém-instalado. A guia **IntelliSense** também mostra mais informações detalhadas. Esteja ciente de que até que esse banco de dados esteja completo, os recursos do IntelliSense, como a verificação automática de conclusão e sintaxe, não estarão ativos no editor para esse pacote.
   > 
   > Visual Studio 2017 versão 15.6 e posteriorusa um método diferente e mais rápido para trabalhar com o IntelliSense, e exibe uma mensagem para esse efeito na guia **IntelliSense.**

## <a name="run-the-program"></a>Execute o programa

1. Agora que [o matplotlib](https://matplotlib.org/) está instalado, execute o programa com (**F5**) ou sem o depurador **(Ctrl**+**F5**) para ver a saída:

   ![Saída de exemplo de matplotlib](media/environments/environments-add-matplotlib3.png)

## <a name="next-step"></a>Próxima etapa

> [!div class="nextstepaction"]
> [Trabalhe com Git](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

## <a name="go-deeper"></a>Aprofunde-se um pouco mais

- [Ambientes do Python](managing-python-environments-in-visual-studio.md)
- [Saiba mais sobre Django no Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [Conheça o Flask no Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)
