---
title: Começando com Python | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543968"
---
# <a name="getting-started-with-python"></a>Introdução ao Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Python Tools for Visual Studio (PTVS), é um [plug-in](https://github.com/Microsoft/ptvs) gratuito e de código aberto para o Visual Studio que uma poderosa experiência de desenvolvimento Python.  
  
## <a name="python-the-language"></a>Python a Linguagem
  
Python é uma linguagem de programação popular que é usada por muitas universidades, cientistas, scripters de aplicativos, desenvolvedores casuais e desenvolvedores profissionais, trabalhando em aplicativos, sites e serviços em nuvem.

Como uma linguagem de programação, Python é:
  
- Confiável.
- Geralmente útil para scripting de programas rápidos, scripting de aplicativos, aplicativos de desktop, servidores web, serviços web e computação científica.
- Fácil de aprender e tem um bom design para incentivar uma boa codificação (muitas universidades usam para cursos de programação introdutória).
- Estilos de programação flexíveis, de suporte, funcionais e orientados a objetos.
- Gratuito e software livre.
- Funciona bem em todos os principais sistemas operacionais.  
- Suportado por muitas bibliotecas gratuitas, úteis e bem projetadas.  
- Suportado por muita documentação, amostras e uma forte comunidade de desenvolvedores.  

Para saber mais sobre o idioma, comece com [Python para Iniciantes](https://www.python.org/about/gettingstarted/) em python.org.

Para instalar o [https://www.python.org/download/](https://www.python.org/download/)próprio Python, visite .

## <a name="python-tools-for-visual-studio"></a>Python Tools para Visual Studio
  
As ferramentas Python para visual studio, que você pode instalar a partir de [visualstudio.com,](https://www.visualstudio.com/explore/python-vs)fornecem os seguintes recursos:  
  
- Suporte para vários intérpretes: várias versões de CPython, IronPython e IPython  
- Um sistema de projeto que seleciona implicitamente uma estrutura de pastas do código Python e também permite o controle explícito, de modo que você possa identificar o código do aplicativo, o código de teste, as páginas da Web, o JavaScript, os scripts de build e assim por diante.  
- Modelos de projeto para console, Web, Azure, ciência de dados e outros tipos de projetos.    
- O Azure SDK para Python (veja abaixo)    
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
- Instalação e demo de recursos (27 min)](https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [Documentação](https://github.com/Microsoft/PTVS/wiki)  

Observe que o Visual Studio não fornece no momento os meios para criar um executável autônomo usando Python, o que significa essencialmente um programa com um interpretador Python incorporado. No entanto, há vários meios dentro da comunidade do Python para fazer isso, conforme descrito em [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency). O CPython também dá suporte a ser inserido em um aplicativo nativo, conforme descrito na postagem do blog [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/) (Usando o arquivo .zip que permite inserção do CPython).
  
## <a name="building-ui-with-python"></a>Construindo UI com Python  

A principal oferta para a construção de uma UI com Python é o [Qt Project](https://www.qt.io/qt-for-application-development/), com vinculações para Python conhecido como [PySide (a vinculação oficial)](https://wiki.qt.io/PySide) (veja também [downloads PySide](https://download.qt.io/official_releases/pyside/.))e [PyQt](https://wiki.python.org/moin/PyQt). No momento, o suporte do Python no Visual Studio não inclui quaisquer ferramentas específicas para desenvolvimento da interface do usuário.

## <a name="azure-sdk-for-python"></a>SDK do Azure para Python
  
O SDK do Azure para Python, que dá suporte a Windows, Mac e Linux, facilita o consumo e o gerenciamento de Serviços do Microsoft Azure. Consulte os recursos a seguir para obter detalhes: 

- Para instalar o SDK, use o [Índice de pacote Python](https://pypi.python.org/pypi/azure) ou siga [Instalar o Python e o SDK](/azure/developer/python/azure-sdk-install) na documentação do Azure. 
- A [Central de desenvolvedores do SDK do Azure para Python](https://azure.microsoft.com/develop/python/) tem muita ajuda, da instalação à documentação, com tutoriais.  Veja alguns destaques:  
- Guias de instruções:
  - [Blob de Armazenamento](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [Fila de armazenamento](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [Tabela de armazenamento](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Filas de Barramento de Serviço](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [Tópicos/assinaturas de ônibus de serviço](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [Gestão de Serviços](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>Computação científica

Além de todas as bibliotecas de cientistas de dados do Python, as Ferramentas Python para Visual Studio dão suporte a IPython e IPython Notebooks, que podem ser hospedados no Azure.

É recomendável obter bibliotecas do IPython e de computação científica (matplotlib, scipy, numpy etc.) da [Universidade da Califórnia, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack).  
  
## <a name="see-also"></a>Consulte também  

[Começando com PTVS: Configuração do Visual Studio](../python/getting-started-with-ptvs-setting-up-visual-studio.md)
[Começando com PTVS: Iniciar codificação (Projetos)](../python/getting-started-with-ptvs-start-coding-projects.md)
[Começando com PTVS: Código](../python/getting-started-with-ptvs-editing-code.md)
de Edição[Começando com PTVS: Depuração](../python/getting-started-with-ptvs-debugging.md)
[Começando com PTVS: Python](../python/getting-started-with-ptvs-interactive-python.md)
Interativo[Começando com PTVS: Construindo um site no Azure](../python/getting-started-with-ptvs-building-a-website-in-azure.md)
