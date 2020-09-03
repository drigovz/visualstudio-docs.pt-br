---
title: Instalando as ferramentas do R
description: Como instalar as Ferramentas do R no Visual Studio 2017 e no Visual Studio 2015, incluindo instalações offline.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
monikerRange: vs-2017
ms.openlocfilehash: 5a09b3f78b929fd60764be36f56c0b580c7a42d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843724"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Como instalar as Ferramentas do R para Visual Studio

Neste artigo:

- [Versões do Visual Studio com suporte](#supported-versions-of-visual-studio)
- [Instalar as RTVS no Visual Studio 2017](#install-rtvs-in-visual-studio-2017)
- [Instalar as RTVS no Visual Studio 2015](#install-rtvs-in-visual-studio-2015)
- [Instalação offline](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> Depois de instalar as Ferramentas do R, talvez você queira configurar o Visual Studio com um layout otimizado para cientista de dados, conforme descrito no artigo [Opções](options-for-r-tools-in-visual-studio.md).

## <a name="supported-versions-of-visual-studio"></a>Versões do Visual Studio com suporte

Há suporte para as RTVS (Ferramentas do R para Visual Studio) no Windows nas edições Enterprise, Professional e Community (gratuita) do [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) e [Visual Studio 2015 Atualização 3 (ou superior)](http://htmlpreview.github.io/?https://github.com/lixzhang/R-MRO-MRS/blob/master/Introduction_to_MRO_and_MRS.html) (download direto).

No momento, não há suporte para as RTVS no Visual Studio para Mac.

As RTVS não serão instaladas se você tiver somente o Shell do Visual Studio incluído com produtos como o Visual Studio Test Professional e o SQL Server Management Studio. O Shell do Visual Studio não tem os componentes necessários para as RTVS.

## <a name="install-rtvs-in-visual-studio-2017"></a>Instalar as RTVS no Visual Studio 2017

1. Execute o instalador do Visual Studio e selecione a opção **Modificar** (para obter detalhes, consulte [Modificar o Visual Studio](../install/modify-visual-studio.md)). Consulte [Instalar o Visual Studio](../install/install-visual-studio.md) se você ainda não tiver o Visual Studio instalado. No Windows 7, certifique-se de que o instalador esteja atualizado para mostrar a versão do Visual Studio 2017 versão *15.2 build 26430.12* ou posterior.

1. Selecione a carga de trabalho **Ciência de dados e aplicativos analíticos**:

    ![Carga de trabalho de ciência de dados e aplicativos analíticos no VS2017](media/installation-data-science-workload.png)

1. Defina quaisquer opções adicionais no lado direito, sob o mesmo nome de carga de trabalho. Por padrão, essa carga de trabalho inclui suporte a F# e Python. Para R, os requisitos mínimos são **Suporte à linguagem R**, **Suporte de runtime para desenvolvimento em R** e **Microsoft R Client**.

O RTVS é instalado em: *% ProgramFiles (x86)% \ Microsoft Visual Studio \<version> \<edition> Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio* , em que *\<version>* normalmente é `2017` *\<edition>* `Community` , `Professional` ou `Enterprise` .

## <a name="install-rtvs-in-visual-studio-2015"></a>Instalar as RTVS no Visual Studio 2015

Com o Visual Studio 2015, você precisa instalar um interpretador de R e as Ferramentas do R separadamente.

### <a name="install-an-r-interpreter"></a>Instalar um interpretador de R

As RTVS requerem uma instalação de 64 bits do R versão 3.2.1 ou posterior em uma ou mais das seguintes fontes:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

O Microsoft R Open e o CRAN R permitem várias versões lado a lado. O Microsoft R Client, no entanto, dá suporte a apenas uma versão e sempre usa a última que foi instalada.

### <a name="install-the-r-tools"></a>Instalar as Ferramentas R

Baixe o RTVS atual para o Visual Studio 2015 do [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.exe) . As RTVS verificam se há uma versão adequada do Visual Studio e ajudam a instalar um interpretador de R, caso isso ainda não tenha sido feito.

> [!Note]
> O instalador autônomo das RTVS funciona apenas com o Visual Studio 2015; com o Visual Studio 2017, instale o suporte ao R por meio da [Carga de trabalho para Aplicativos de ciência de dados e análise](#install-rtvs-in-visual-studio-2017) conforme descrito anteriormente.

As RTVS para Visual Studio 2015 estão instaladas em: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Instalação offline do Visual Studio e das RTVS

A instalação offline é adequada para computadores que não estão conectados à Internet:

1. Vá para [Criar uma instalação offline do Visual Studio 2017](../install/create-an-offline-installation-of-visual-studio.md).

1. Se você usar o Visual Studio 2015, selecione **2015** no seletor acima do sumário.

1. Siga as instruções para criar uma instalação offline na página da Web.

1. Para o Visual Studio 2015, baixe os instaladores offline do RTVS de [https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_2017-12-18.1.zip) e [https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip](https://rtvs.blob.core.windows.net/download/RTVS_Remote_2017-12-12.1.zip) .

1. Instale o Visual Studio e as RTVS dos instaladores offline.

## <a name="see-also"></a>Confira também

- [Introdução ao R](getting-started-with-r.md)
- [Projetos de exemplo das Ferramentas do R](getting-started-samples.md)
- [Ajuda nas Ferramentas do R](getting-started-help.md)
- [Opções de Ferramentas R](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning Server (anteriormente conhecido como R Server)](/machine-learning-server/)
