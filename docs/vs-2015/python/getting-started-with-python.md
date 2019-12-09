---
title: Introdução com Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 21e724e585f2a5bf0e1fe2a6b70f89c1bd5f5eec
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298193"
---
# <a name="getting-started-with-python"></a>Introdução ao Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Ferramentas Python para Visual Studio (PTVS), é um plug-in gratuito de software livre para o Visual [Studio, que](https://github.com/Microsoft/ptvs) é uma experiência de desenvolvimento eficiente em Python.  
  
## <a name="python-the-language"></a>Python o idioma
  
O Python é uma linguagem de programação popular usada por muitas universidades, cientistas, criadores de scripts de aplicativos, desenvolvedores casuais e desenvolvedores profissionais, trabalhando em aplicativos, sites e serviços de nuvem.

Como uma linguagem de programação, o Python é:
  
- Confiável.
- Geralmente útil para scripts de programas rápidos, scripts de aplicativos, aplicativos de área de trabalho, servidores Web, Web Services e computação científica.
- Fácil de aprender e tem um bom design para incentivar a boa codificação (muitas universidades o utilizam para cursos introdutórios de programação).
- Estilos de programação flexíveis, com suporte imperativos, funcionais e orientados a objeto.
- Gratuito e software livre.
- É executado bem em todos os principais sistemas operacionais.  
- Com suporte de muitas bibliotecas gratuitas, úteis e bem projetadas.  
- Com suporte de muitas documentações, exemplos e uma forte comunidade de desenvolvedores.  

Para saber mais sobre a linguagem, comece com [Python para iniciantes](https://www.python.org/about/gettingstarted/) no Python.org.

Para instalar o Python em si, visite [https://www.python.org/download/](https://www.python.org/download/).

## <a name="python-tools-for-visual-studio"></a>Ferramentas Python para o Visual Studio
  
O Ferramentas Python para Visual Studio, que você pode instalar do [VisualStudio.com](https://www.visualstudio.com/explore/python-vs), fornece os seguintes recursos:  
  
- Suporte para vários intérpretes: várias versões de CPython, IronPython e IPython  
- Um sistema de projeto que seleciona implicitamente uma estrutura de pastas do código Python e também permite o controle explícito, de modo que você possa identificar o código do aplicativo, o código de teste, as páginas da Web, o JavaScript, os scripts de build e assim por diante.  
- Modelos de projeto para console, Web, Azure, ciência de dados e outros tipos de projetos.    
- O SDK do Azure para Python (veja abaixo)    
- Recursos de compreensão de código e edição avançada, incluindo coloração de sintaxe, preenchimento automático em todo o seu código e bibliotecas, ajuda com assinatura, modo de exibição de classe, Ir para Definição, Localizar Todas as Referências, refatoração e muito mais.    
- Uma Janela Interativa (REPL)
- IPython com visualizações de dados.
- Suporte para IronPython e .NET/WPF.    
- Depuração avançada sem um projeto do Visual Studio, a capacidade de depurar um executável existente, depuração de modo misto, depuração remota para Linux/Windows/Mac e depuração dentro da Janela Interativa.   
- Ferramentas de criação de perfil.  
- Ferramentas de teste.  
  
Os recursos a seguir o ajudarão a começar:

- [Guia de instalação](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Introdução e vídeos de aprofundamento](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)  
- Demonstração de instalação e recursos (27 min)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Documentação](https://github.com/Microsoft/PTVS/wiki)  

Observe que o Visual Studio não no momento fornece os meios para criar um executável autônomo usando Python, o que essencialmente significa um programa com um intérprete Python incorporado. No entanto, há vários meios dentro da comunidade do Python para fazer isso, conforme descrito em [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). O CPython também dá suporte a ser inserido em um aplicativo nativo, conforme descrito na postagem do blog [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Usando o arquivo .zip que permite inserção do CPython).
  
## <a name="building-ui-with-python"></a>Criando interface do usuário com Python  

A principal oferta para criar uma interface do usuário com Python é o [projeto Qt](https://www.qt.io/qt-for-application-development/), com associações para o Python conhecido como [pyside (a associação oficial)](https://wiki.qt.io/PySide) (também consulte [downloads do pyside](https://download.qt.io/official_releases/pyside/.)) e [PyQt](https://wiki.python.org/moin/PyQt). No momento, o suporte do Python no Visual Studio não inclui quaisquer ferramentas específicas para desenvolvimento da interface do usuário.

## <a name="azure-sdk-for-python"></a>SDK do Azure para Python
  
O SDK do Azure para Python, que dá suporte a Windows, Mac e Linux, facilita o consumo e o gerenciamento de Serviços do Microsoft Azure. Consulte os recursos a seguir para obter detalhes: 

- Para instalar o SDK, use o [Índice de pacote Python](https://pypi.python.org/pypi/azure) ou siga [Instalar o Python e o SDK](https://docs.microsoft.com/azure/python/python-sdk-azure-install) na documentação do Azure. 
- A [Central de desenvolvedores do SDK do Azure para Python](https://azure.microsoft.com/develop/python/) tem muita ajuda, da instalação à documentação, com tutoriais.  Veja alguns destaques:  
- Guias de instruções:
  - [Armazenamento de blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Fila de armazenamento](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabela de página](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Filas do Barramento de Serviço](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Tópicos/assinaturas do Barramento de Serviço](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Gerenciamento de serviços](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Computação científica

Além de todas as bibliotecas de cientistas de dados do Python, as Ferramentas Python para Visual Studio dão suporte a IPython e IPython Notebooks, que podem ser hospedados no Azure.

É recomendável obter bibliotecas do IPython e de computação científica (matplotlib, scipy, numpy etc.) da [Universidade da Califórnia, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Consulte também  

[Introdução ao PTVS: instalando o Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Introdução ao PTVS: iniciar a codificação (projetos)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Introdução ao PTVS: editando código](../python/getting-started-with-ptvs-editing-code.md)
[Introdução ao PTVS: depurando](../python/getting-started-with-ptvs-debugging.md)
[Introdução ao PTVS: Python interativo](../python/getting-started-with-ptvs-interactive-python.md)
[Introdução ao PTVS: compilando um site no Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
