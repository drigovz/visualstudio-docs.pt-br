---
title: Suporte do Python no Visual Studio no Windows
titleSuffix: ''
description: Resumo dos recursos do Python no Visual Studio, que fazem dele o melhor IDE do Python no Windows (também conhecido como PTVS, Ferramentas Python para Visual Studio).
ms.date: 06/05/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 24bbfd276b30444742b329f30c346ac1857c2cc9
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154962"
---
# <a name="work-with-python-in-visual-studio-on-windows"></a>Trabalhar com Python no Visual Studio no Windows

O Python é uma linguagem de programação popular confiável, flexível, fácil de aprender, de uso gratuito em todos os sistemas operacionais e com suporte em uma sólida comunidade de desenvolvedores e várias bibliotecas gratuitas. O Python permite todas as formas de desenvolvimento, incluindo aplicativos Web, serviços Web, aplicativos de área de trabalho, scripts e computação científica, além de ser usado por diversas universidades, cientistas, desenvolvedores amadores e também desenvolvedores profissionais. Saiba mais sobre a linguagem em [python.org](https://www.python.org) e em [Python para iniciantes](https://www.python.org/about/gettingstarted/).

O Visual Studio é um IDE do Python poderoso no Windows. O Visual Studio é compatível com [software livre](https://github.com/Microsoft/ptvs) para a linguagem Python por meio de cargas de trabalho de **Desenvolvimento em Python** e de **Ciência de Dados** (Visual Studio 2017 e posteriores) e a extensão gratuita das Ferramentas Python para Visual Studio (Visual Studio 2015 e anteriores).

No momento, o Python não tem suporte no Visual Studio para Mac, mas está disponível no Mac e no Linux por meio do Visual Studio Code (veja as [perguntas e respostas](#questions-and-answers)).

Para começar:

- Siga as [instruções de instalação](installing-python-support-in-visual-studio.md) para configurar a carga de trabalho Python.
- Familiarize-se com os recursos do Python no Visual Studio examinando as seções neste artigo.
::: moniker range="vs-2017"
- Realize ou mais Guias de Início Rápido para criar um projeto. Se você não tiver certeza, comece com [Criar um aplicativo Web com o Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
::: moniker range=">=vs-2019"
- Realize ou mais Guias de Início Rápido para criar um projeto. Se você não tiver certeza, comece com [Início Rápido: Abrir e executar código Python em uma pasta](quickstart-05-python-visual-studio-open-folder.md) ou [Criar um aplicativo Web com o Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json).
::: moniker-end
- Siga o tutorial [Trabalhar com o Python no Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md) para ter uma experiência completa de ponta a ponta.

::: moniker range=">=vs-2019"
> [!Note]
> O Visual Studio dá suporte ao Python versão 2.7, bem como à versão 3.5 e posterior. Embora seja possível usar o Visual Studio para editar código escrito em outras versões do Python, essas versões não são oficialmente aceitas, e recursos como o IntelliSense e a depuração podem não funcionar.
::: moniker-end

## <a name="support-for-multiple-interpreters"></a>Suporte para vários interpretadores

A janela **Ambientes do Python** do Visual Studio (mostrada abaixo em uma exibição ampla, expandida) fornece um único local para gerenciar todos os ambientes do Python globais, os ambientes do Conda e os ambientes virtuais. O Visual Studio detecta automaticamente as instalações do Python em locais padrão e permite que você configure instalações personalizadas. Em cada ambiente, é possível gerenciar pacotes, abrir uma janela interativa desse ambiente e acessar as pastas do ambiente facilmente.

::: moniker range="vs-2017"
![Exibição expandida da janela Ambientes do Python](media/environments/environments-expanded-view.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Exibição expandida da janela Ambientes do Python](media/environments/environments-expanded-view-2019.png)
::: moniker-end

Use o comando **Abrir janela interativa** para executar o Python de maneira interativa no contexto do Visual Studio. Use o comando **Abrir no PowerShell** para abrir uma janela Comando separada na pasta do ambiente selecionado. Nessa janela Comando, você pode executar qualquer script de Python.

Para saber mais:

- [Gerenciar ambientes do Python](managing-python-environments-in-visual-studio.md)
- [Referência aos ambientes do Python](python-environments-window-tab-reference.md)

## <a name="rich-editing-intellisense-and-code-comprehension"></a>Edição avançada, IntelliSense e compreensão do código

O Visual Studio oferece um editor de Python de primeira classe, incluindo coloração de sintaxe, preenchimento automático em todo o código e em todas as bibliotecas, formatação de código, ajuda de assinatura, refatoração, dicas de tipo e linting. O Visual Studio também fornece recursos exclusivos como modo de exibição de classe, **Ir para Definição**, **Localizar Todas as Referências** e snippets de código. A integração direta com a [janela Interativa](#interactive-window) ajuda você a desenvolver rapidamente um código Python que já está salvo em um arquivo.

![Preenchimento de código para código Python no Visual Studio](media/code-editing-completions-simple.png)

Para saber mais:

- Documentação: [Editar o código Python](editing-python-code-in-visual-studio.md)
- Documentação: [Formatar código](formatting-python-code.md)
- Documentação: [Refatorar o código](refactoring-python-code.md)
- Documentação: [Usar um linter](linting-python-code.md)
- Documentação de funcionalidades gerais do Visual Studio: [Recursos do Editor de Códigos](../ide/writing-code-in-the-code-and-text-editor.md)

## <a name="interactive-window"></a>Janela Interativa

Para cada ambiente do Python conhecido para o Visual Studio, você pode abrir facilmente o mesmo ambiente interativo (REPL) de um interpretador de Python diretamente no Visual Studio, em vez de usar um prompt de comando separado. Também é possível mudar facilmente de ambiente. (Para abrir um prompt de comando separado, selecione o ambiente desejado na janela **Ambientes do Python** e, em seguida, selecione o comando **Abrir no PowerShell**, conforme explicado anteriormente em [Suporte para vários intérpretes](#support-for-multiple-interpreters).)

![Janela interativa do Python no Visual Studio](media/interactive-window.png)

O Visual Studio também fornece uma forte integração entre o editor de código Python e a janela **Interativa**. Para facilitar, o atalho de teclado **Ctrl**+**Enter** envia a linha de código (ou bloco de código) atual no editor para a janela **Interativa** e passa para a próxima linha (ou bloco). **Ctrl**+**Enter** permite percorrer o código facilmente sem precisar executar o depurador. Também é possível enviar o código escolhido para a janela **Interativa** com o mesmo pressionamento de tecla e colar o código facilmente da janela **Interativa** para o editor. Juntos, esses recursos permitem que você elabore detalhes de um segmento de código na janela **Interativa** e salve os resultados facilmente em um arquivo no editor.

O Visual Studio também é compatível com IPython/Jupyter no REPL, incluindo gráficos embutidos, .NET e WPF (Windows Presentation Foundation).

Para saber mais:

- [Janela Interativa](python-interactive-repl-in-visual-studio.md)
- [IPython no Visual Studio](interactive-repl-ipython.md)

## <a name="project-system-and-project-and-item-templates"></a>Sistema de projeto e modelos de projeto e de item

::: moniker range=">=vs-2019"
> [!Note]
> O Visual Studio 2019 dá suporte à abertura de uma pasta que contém o código do Python e à execução do código sem criar arquivos de projeto e solução do Visual Studio. Para obter mais informações, confira [Início Rápido: Abrir e executar código Python em uma pasta](quickstart-05-python-visual-studio-open-folder.md). No entanto, há benefícios em usar um arquivo de projeto, conforme explicado nesta seção.
::: moniker-end

O Visual Studio ajuda você a gerenciar a complexidade de um projeto à medida que ele cresce ao longo do tempo. Um *projeto do Visual Studio* é muito mais do que uma estrutura de pastas: ele inclui um reconhecimento de como diferentes arquivos são usados e como se relacionam entre si. O Visual Studio ajuda a diferenciar código do aplicativo, código de teste, páginas da Web, JavaScript, scripts de build e assim por diante, o que permite usar os recursos apropriados para cada arquivo. Além disso, uma solução do Visual Studio ajuda você a gerenciar vários projetos relacionados, como um projeto Python e um projeto de extensão C++.

![Uma solução do Visual Studio que contém projetos Python e C++](media/projects-solution-explorer-two-projects.png)

Modelos de projeto e de item automatizam o processo de configuração de diferentes tipos de projetos e arquivos, economizando tempo e eliminando a necessidade de gerenciar detalhes complexos e propensos a erros. O Visual Studio fornece modelos para projetos da Web, do Azure, de ciência de dados, de console e de outros tipos, juntamente com modelos de arquivos, como classes do Python, testes de unidade, configuração da Web do Azure, HTML e até mesmo aplicativos Django.

[![Modelos de projeto e de item do Python no Visual Studio](media/project-and-item-templates.png)](media/project-and-item-templates.png#lightbox)

Para saber mais:

- Documentação: [Gerenciar projetos do Python](managing-python-projects-in-visual-studio.md)
- Documentação: [Referência de modelos de item](python-item-templates.md)
- Documentação: [Modelos de projeto do Python](managing-python-projects-in-visual-studio.md#project-templates)
- Documentação: [Trabalhar com o C++ e o Python](working-with-c-cpp-python-in-visual-studio.md)
- Documentação de funcionalidades gerais do Visual Studio: [Modelos de projeto e item](../ide/creating-project-and-item-templates.md#visual-studio-templates)
- Documentação de funcionalidades gerais do Visual Studio: [Soluções e projetos no Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)

## <a name="full-featured-debugging"></a>Depuração completa

Um dos pontos fortes do Visual Studio é seu depurador avançado. Para Python especificamente, o Visual Studio inclui depuração de modo misto Python/C++, depuração remota no Linux, depuração dentro da janela **Interativa** e depuração de testes de unidade do Python.

![Depurador do Visual Studio para Python mostrando um pop-up de exceção](media/debugging-exception-popup.png)

::: moniker range=">=vs-2019"
No Visual Studio 2019, é possível executar e depurar código sem a necessidade de um arquivo de projeto do Visual Studio. Confira [Início Rápido: abrir e executar código Python em uma pasta](quickstart-05-python-visual-studio-open-folder.md) para ter um exemplo.
::: moniker-end

Para saber mais:

- Documentação: [Depurar o Python](debugging-python-in-visual-studio.md)
- Documentação: [Depuração de modo misto do Python/C++](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- Documentação: [Depuração remota no Linux](debugging-python-code-on-remote-linux-machines.md)
- Documentação de funcionalidades gerais do Visual Studio: [Tour de funcionalidades do depurador do Visual Studio](../debugger/debugger-feature-tour.md)

## <a name="profiling-tools-with-comprehensive-reporting"></a>Ferramentas de criação de perfil com relatórios abrangentes

A criação de perfil explora como o tempo está sendo gasto no aplicativo. O Visual Studio permite a criação de perfil com interpretadores baseados em CPython e inclui a capacidade de comparar o desempenho entre diferentes execuções de criação de perfil.

[![Resultados do criador de perfil do Visual Studio para um projeto Python](media/profiling-results.png)](media/profiling-results.png#lightbox)

Para saber mais:

- Documentação: [Ferramentas de criação de perfil do Python](profiling-python-code-in-visual-studio.md)
- Documentação de funcionalidades gerais do Visual Studio: [Tour de funcionalidades de criação de perfil](../profiling/profiling-feature-tour.md). (Nem todos os recursos de criação de perfil do Visual Studio estão disponíveis para Python).

## <a name="unit-testing-tools"></a>Ferramentas de teste de unidade

Descubra, execute e gerencie testes no **Gerenciador de Testes** do Visual Studio e depure testes de unidade com facilidade.

![Depurando um teste de unidade do Python no Visual Studio](media/unit-test-debugging.png)

Para saber mais:

- Documentação: [Ferramentas de teste de unidade do Python](unit-testing-python-in-visual-studio.md)
- Documentação de funcionalidades gerais do Visual Studio: [Executar teste de unidade no código](../test/unit-test-your-code.md).

## <a name="azure-sdk-for-python"></a>SDK do Azure para Python

As bibliotecas do Azure para Python simplificam o consumo de serviços do Azure em aplicativos do Windows, do Mac OS X e do Linux. Você pode usá-las para criar e gerenciar recursos do Azure, bem como para se conectar aos serviços do Azure. 

Para obter mais informações, confira [SDK do Azure para Python](/azure/python/) e [Bibliotecas do Azure para Python](/azure/python/python-sdk-azure-overview).

## <a name="questions-and-answers"></a>Perguntas e respostas

**P. O suporte para Python está disponível com o Visual Studio para Mac?**

R. Não no momento, mas você pode votar na solicitação em [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/content/idea/351820/python-tools-for-visual-studio-mac.html). A documentação do [Visual Studio para Mac](/visualstudio/mac/) identifica os tipos atuais de desenvolvimento aos quais dá suporte. Enquanto isso, o Visual Studio Code no Windows, Mac e Linux [funciona bem com o Python por meio das extensões disponíveis](https://code.visualstudio.com/docs/languages/python).

**P. O que pode ser usado para criar a interface do usuário com o Python?**

R. A oferta principal nessa área é o [Projeto Qt](https://www.qt.io/qt-for-application-development/), com associações de Python conhecidas como [PySide (a associação oficial)](https://wiki.qt.io/PySide) (consulte também [Downloads do PySide](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). No momento, o suporte do Python no Visual Studio não inclui quaisquer ferramentas específicas para desenvolvimento da interface do usuário.

**P. Um projeto do Python pode produzir um executável autônomo?**

R. Geralmente, o Python é uma linguagem interpretada, com a qual o código é executado sob demanda em um ambiente compatível com o Python, como o Visual Studio e servidores Web. No momento, o Visual Studio não fornece meios para criar um executável autônomo, o que, basicamente, é um programa com um interpretador de Python incorporado. No entanto, a comunidade do Python forneceu maneiras diferentes de criar executáveis, conforme descrito em [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). O CPython também dá suporte a ser inserido em um aplicativo nativo, conforme descrito na postagem do blog [Usar o arquivo .zip que permite inserção do CPython](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/).

::: moniker range="<=vs-2017"

## <a name="feature-support"></a>Suporte a recursos

Os recursos do Python podem ser instalados nas seguintes edições do Visual Studio, conforme é descrito no [guia de instalação](installing-python-support-in-visual-studio.md):

- [Visual Studio 2019 (todas as edições)](https://visualstudio.microsoft.com/vs/)
- Visual Studio 2017 (todas as edições)
- Visual Studio 2015 (todas as edições)
- Visual Studio 2013 Community Edition
- Visual Studio 2013 Express para Web, Atualização 2 ou posterior
- Visual Studio 2013 Express para Área de Trabalho, Atualização 2 ou posterior
- Visual Studio 2013 (edição Pro ou superior)
- Visual Studio 2012 (edição Pro ou superior)
- Visual Studio 2010 SP1 (edição Pro ou superior; o .NET 4.5 é necessário)

O Visual Studio 2015 e as versões anteriores estão disponíveis em [visualstudio.microsoft.com/vs/older-downloads/](https://visualstudio.microsoft.com/vs/older-downloads/).

> [!Important]
> Somente há suporte e manutenção completos para os recursos na versão mais recente do Visual Studio. Os recursos estão disponíveis nas versões mais antigas, mas não recebem manutenção ativa.

|          Suporte para Python          |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|   Gerenciar vários interpretadores   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Detecção automática de interpretadores populares | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Adição de interpretadores personalizados      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Ambientes Virtuais       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         PIP/Fácil instalação         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Sistema de projeto         |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ |      2012 Pro+       | 2010 SP1 Pro+ |
|--------------------------------|----------|----------|-----------|--------------|----------|-----------|----------------------|---------------|
| Novo projeto com base em um código existente | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Mostrar todos os arquivos         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|         Controle do código-fonte         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  |       &#10004;       |   &#10004;    |
|        Integração com o Git         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;<sup>1</sup> |   &#10007;    |

<br/>

|           Edição            |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Realce de sintaxe      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Preenchimento automático         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Ajuda da assinatura        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|          Informações rápidas          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Modo de exibição de classe/pesquisador de objetos   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Barra de navegação        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Ir para Definição       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Navegar para          | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|     Localizar Todas as Referências      | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Recuo automático       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|       Formatação de código        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Refatorar – renomear       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Refatorar – extrair método   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Refatorar – adicionar ou remover importação | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|            PyLint            | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Janela Interativa     |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|----------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Janela Interativa     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| IPython com grafos embutidos | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|               Desktop               |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|     Aplicativo de console/do Windows     | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| WPF do IronPython (com o designer XAML) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|      Windows Forms do IronPython       | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Web         |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Projeto Web do Django  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projeto Web do Bottle  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|  Projeto Web do Flask  | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
| Projeto Web genérico | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|         Azure          |   2017+   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       |      2012 Pro+       |    2010 SP1 Pro+     |
|------------------------|----------|----------|-----------|--------------|----------------------|----------------------|----------------------|----------------------|
|   Implantar no site da Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       |       &#10004;       | &#10004;<sup>2</sup> |
|   Implantar na função Web   | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Implantar na função de trabalho  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
| Execução no emulador do Azure  |    ?     |    ?     |     ?     |   &#10007;   | &#10004;<sup>4</sup> | &#10004;<sup>4</sup> | &#10004;<sup>3</sup> |       &#10007;       |
|    Depuração remota    | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>6</sup> | &#10004;<sup>8</sup> | &#10004;<sup>8</sup> |       &#10007;       |
| Anexar o Gerenciador de Servidores | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>7</sup> | &#10004;<sup>7</sup> |       &#10007;       |       &#10007;       |

<br/>

|           Modelos do Django           |   2017+   |   2015   | 2013 Comm | 2013 Desktop |       2013 Web       |      2013 Pro+       | 2012 Pro+ | 2010 SP1 Pro+ |
|--------------------------------------|----------|----------|-----------|--------------|----------------------|----------------------|-----------|---------------|
|              Depuração               | &#10004; | &#10004; | &#10004;  |   &#10007;   |       &#10004;       |       &#10004;       | &#10004;  |   &#10004;    |
|            Preenchimento automático             | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10004;  |   &#10004;    |
| Preenchimento automático para CSS e JavaScript | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10004;<sup>5</sup> | &#10004;<sup>5</sup> | &#10007;  |   &#10007;    |

<br/>

|                  Depuração                  |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------------------------------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
|                  Depuração                  | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|         Depuração sem um projeto         | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |
|        Depuração – anexação à edição        | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|            Depuração de modo misto             | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
| Depuração remota (Windows, Mac OS X, Linux) | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |
|          Depurar janela Interativa           | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

<a name="matrix-profiling"></a>

| Criação de perfil |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|-----------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Criação de perfil | &#10004; | &#10004; | &#10004;  |   &#10007;   | &#10007; | &#10004;  | &#10004;  |   &#10004;    |

<br/>

|     Teste      |   2017+   |   2015   | 2013 Comm | 2013 Desktop | 2013 Web | 2013 Pro+ | 2012 Pro+ | 2010 SP1 Pro+ |
|---------------|----------|----------|-----------|--------------|----------|-----------|-----------|---------------|
| Gerenciador de testes | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|   Executar teste    | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |
|  Depurar teste   | &#10004; | &#10004; | &#10004;  |   &#10004;   | &#10004; | &#10004;  | &#10004;  |   &#10007;    |

<br/>

1. O suporte do Git para o Visual Studio 2012 está disponível na extensão Ferramentas do Visual Studio para Git, disponível no [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=TFSPowerToolsTeam.VisualStudioToolsforGit).

1. A implantação no Site do Azure exige o [SDK do Azure para .NET 2.1 – Visual Studio 2010 SP1](https://go.microsoft.com/fwlink/?LinkId=313855). Versões posteriores não dão suporte ao Visual Studio 2010.

1. O suporte à Função Web e à Função de Trabalho do Azure exige o [SDK do Azure para .NET 2.3 – VS 2012](https://go.microsoft.com/fwlink/?LinkId=323511) ou posterior.

1. O suporte à Função Web e à Função de Trabalho do Azure exige o [SDK do Azure para .NET 2.3 – VS 2013](https://go.microsoft.com/fwlink/?LinkId=323510) ou posterior.

1. O editor de modelos do Django no Visual Studio 2013 apresenta alguns problemas conhecidos que foram resolvidos com a instalação da Atualização 2.

1. Exige o Windows 8 ou posterior. O Visual Studio 2013 Express para Web não tem a caixa de diálogo **Anexar ao Processo**, mas a depuração remota do Site do Azure ainda é possível com o comando **Anexar Depurador (Python)** no **Gerenciador de Servidores**. A depuração remota exige o [SDK do Azure para .NET 2.3 – Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) ou posterior.

1. Exige o Windows 8 ou posterior. O comando **Anexar Depurador (Python)** no **Gerenciador de Servidores** exige o [SDK do Azure para .NET 2.3 - Visual Studio 2013](https://go.microsoft.com/fwlink/?LinkId=323510) ou posterior.

1. Exige o Windows 8 ou posterior.
::: moniker-end
