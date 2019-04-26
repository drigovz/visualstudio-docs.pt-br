---
title: IDs de carga de trabalho e de componente do Visual Studio
titleSuffix: ''
description: Usar as IDs de carga de trabalho e de componente para instalar o Visual Studio usando uma linha de comando ou para especificar como uma dependência em um manifesto do VSIX
keywords: ''
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 03/02/2019
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.custom: seodec18
ms.assetid: 34e19ef1-abfb-44fd-aad2-33c5d7874482
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 02229fd346ec1ead65e778fcce3ab6cb307e2656
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951253"
---
# <a name="visual-studio-workload-and-component-ids"></a>IDs de carga de trabalho e de componente do Visual Studio

Clique nos nomes de edição na tabela a seguir para ver as IDs de carga de trabalho e de componente disponíveis que você precisa para instalar o Visual Studio usando uma linha de comando ou para especificar como uma dependência em um manifesto do VSIX.

::: moniker range="vs-2017"

**Atualizado para a [versão 15.9](/visualstudio/releasenotes/vs2017-relnotes/)**

| **Edição** | **ID** | **Descrição** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2017](workload-component-id-vs-enterprise.md?vs-2017) | Microsoft.VisualStudio.Product.Enterprise | Solução Microsoft DevOps para produtividade e coordenação entre equipes de qualquer tamanho |
| [Visual&nbsp;Studio Professional&nbsp;2017](workload-component-id-vs-professional.md?vs-2017) | Microsoft.VisualStudio.Product.Professional | Ferramentas para desenvolvedores profissionais e serviços para equipes pequenas |
| [Visual&nbsp;Studio Community&nbsp;2017](workload-component-id-vs-community.md) | Microsoft.VisualStudio.Product.Community | IDE gratuita e completa para estudantes, desenvolvedores individuais e de software livre |
| [Team Explorer&nbsp;para&nbsp;Visual Studio&nbsp;2017](workload-component-id-vs-team-explorer.md?vs-2017) | Microsoft.VisualStudio.Product.TeamExplorer | Interaja com o Team Foundation Server e com o Azure DevOps Services sem um conjunto de ferramentas de desenvolvedor do Visual Studio |
| [Visual Studio 2017 Desktop Express](workload-component-id-vs-express.md?vs-2017) | Microsoft.VisualStudio.Product.WDExpress | Compile aplicativos Gerenciados e Nativos como WPF, WinForms e Win32 com edição de código com reconhecimento de sintaxe, controle do código-fonte e gerenciamento de item de trabalho. Inclui suporte para o C#, Visual Basic e Visual C++. |
| [Ferramentas de Build&nbsp;do&nbsp;Visual Studio&nbsp;2017](workload-component-id-vs-build-tools.md?vs-2017) | Microsoft.VisualStudio.Product.BuildTools | As Ferramentas de Build do Visual Studio permitem que você compile aplicativos baseados em MSBuild nativos e gerenciados, sem exigir o IDE do Visual Studio. Há opções para instalar compiladores e bibliotecas do Visual C++, além do suporte a C++/CLI, ATL e MFC. |
| [Test Agent&nbsp;do&nbsp;Visual Studio&nbsp;2017](workload-component-id-vs-test-agent.md?vs-2017)  | Microsoft.VisualStudio.Product.TestAgent | Dá suporte à execução de testes automatizados e carrega testes remotamente |
| [Test Controller&nbsp;do&nbsp;Microsoft Visual Studio 2017](workload-component-id-vs-test-controller.md?vs-2017) | Microsoft.VisualStudio.Product.TestController | Distribuir testes automatizados para vários computadores |
| [Visual&nbsp;Studio Test&nbsp;Professional&nbsp;2017](workload-component-id-vs-test-professional.md?vs-2017) | Microsoft.VisualStudio.Product.TestProfessional | Visual Studio Test Professional 2017 |
| [Visual&nbsp;Studio Feedback&nbsp;Client&nbsp;2017](workload-component-id-vs-feedback-client.md?vs-2017) | Microsoft.VisualStudio.Product.FeedbackClient | Visual Studio Feedback Client 2017 |

Para obter mais informações sobre como usar essas listas, confira a página [Usar parâmetros de linha de comando para instalar o Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) e a página [Como: Migrar projetos de extensibilidade para o Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2017).

::: moniker-end

::: moniker range="vs-2019"

**Atualizado para o [Visual Studio 2019 RC](/visualstudio/releases/2019/release-notes/)**

| **Edição** | **ID** | **Descrição** |
| ----------- | ------ | --------------- |
| [Visual&nbsp;Studio Enterprise&nbsp;2019](workload-component-id-vs-enterprise.md?vs-2019) | Microsoft.VisualStudio.Product.Enterprise | Solução Microsoft DevOps para produtividade e coordenação entre equipes de qualquer tamanho |
| [Visual&nbsp;Studio Professional&nbsp;2019](workload-component-id-vs-professional.md?vs-2019) | Microsoft.VisualStudio.Product.Professional | Ferramentas para desenvolvedores profissionais e serviços para equipes pequenas |
| [Visual&nbsp;Studio Community&nbsp;2019](workload-component-id-vs-community.md?vs-2019) | Microsoft.VisualStudio.Product.Community | IDE gratuita e completa para estudantes, desenvolvedores individuais e de software livre |
| [Visual&nbsp;Studio Team&nbsp;Explorer&nbsp;2019](workload-component-id-vs-team-explorer.md?vs-2019) | Microsoft.VisualStudio.Product.TeamExplorer | Interaja com o Team Foundation Server e com o Azure DevOps Services sem um conjunto de ferramentas de desenvolvedor do Visual Studio |
| Ferramentas de[Build do&nbsp;Visual&nbsp;Studio&nbsp;2019](workload-component-id-vs-build-tools.md?vs-2019) | Microsoft.VisualStudio.Product.BuildTools | As Ferramentas de Build do Visual Studio permitem que você compile aplicativos baseados em MSBuild nativos e gerenciados, sem exigir o IDE do Visual Studio. Há opções para instalar compiladores e bibliotecas do Visual C++, além do suporte a C++/CLI, ATL e MFC. |
| Test[Agent do&nbsp;Visual&nbsp;Studio&nbsp;2019](workload-component-id-vs-test-agent.md?vs-2019)  | Microsoft.VisualStudio.Product.TestAgent | Dá suporte à execução de testes automatizados e carrega testes remotamente |
| [Visual&nbsp;Studio Load&nbsp;Test&nbsp;Controller 2019](workload-component-id-vs-test-controller.md?vs-2019) | Microsoft.VisualStudio.Product.TestController | Distribuir testes automatizados para vários computadores |

Para obter mais informações sobre como usar essas listas, confira a página [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) e a página [Como: Migrar projetos de extensibilidade para o Visual Studio](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md?view=vs-2019).

> [!NOTE]
> Para obter uma lista de IDs de carga de trabalho e de componente para a versão anterior, confira [IDs de carga de trabalho e de componente do Visual Studio 2017](workload-and-component-ids.md?view=vs-2017)

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Guia do administrador do Visual Studio para o Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Exemplos de parâmetro de linha de comando](command-line-parameter-examples.md)
* [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)
