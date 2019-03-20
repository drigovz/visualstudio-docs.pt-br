---
title: Instalar versões do Visual Studio lado a lado
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1f2969fe93ab2623b1f8406f6eaa0ce35c454202
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160531"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Instalar versões do Visual Studio lado a lado

É possível instalar o Visual Studio em um computador que já tenha uma versão anterior dele instalada.

::: moniker range="vs-2017"

Antes de instalar as versões lado a lado, revise as seguintes condições:

* Se você usar o Visual Studio 2017 para abrir uma solução que foi criada no Visual Studio 2015, você poderá, posteriormente, abrir e modificar a solução novamente na versão anterior desde que você não tenha implementado quaisquer recursos que são específicos do Visual Studio 2017.

* Se você tentar usar o Visual Studio 2017 para abrir uma solução que foi criada no Visual Studio 2015 ou em uma versão anterior, talvez você precise alterar seus projetos e arquivos para que fiquem compatíveis com o Visual Studio 2017. Para obter mais informações, veja a página [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017).

::: moniker-end

::: moniker range=">= vs-2019"

Antes de instalar as versões lado a lado, revise as seguintes condições:

* Se você usar o Visual Studio 2019 para abrir uma solução que foi criada no Visual Studio 2017, você poderá, posteriormente, abrir e modificar a solução novamente na versão anterior desde que você não tenha implementado quaisquer recursos que são específicos do Visual Studio 2019.

* Se você tentar usar o Visual Studio 2019 para abrir uma solução que foi criada no Visual Studio 2017 ou em uma versão anterior, talvez você precise alterar seus projetos e arquivos para que fiquem compatíveis com o Visual Studio 2019. Para obter mais informações, veja a página [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-upgrade-visual-studio-projects-2019.md).

::: moniker-end

* Se você desinstalar uma versão do Visual Studio em um computador que tem mais de uma versão instalada, as associações de arquivo do Visual Studio serão removidas para todas as versões.

* O Visual Studio não atualiza automaticamente extensões porque nem todas as extensões são compatíveis. Você deverá reinstalar as extensões do [Visual Studio Marketplace](http://go.microsoft.com/fwlink/?LinkId=178891) ou do fornecedor de software.

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versões do .NET Framework e instalações lado a lado

Os projetos Visual Basic, Visual C# e Visual F# usam a opção **Estrutura de Destino** no **Designer de Projeto** para especificar qual versão do .NET Framework um projeto usa. Para um projeto do C++, é possível alterar manualmente a estrutura de destino alterando o arquivo .vcxproj. Para obter mais informações, veja a página [Compatibilidade de versão no .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Ao criar um projeto, você pode especificar a qual versão do .NET Framework o projeto é direcionado na lista **.NET Framework** na caixa de diálogo **Novo Projeto**.

Para informações específicas do idioma, consulte o tópico apropriado na tabela a seguir.

::: moniker range="vs-2017"

| Idioma | Tópico |
|--------------|-----------|
| Visual Basic | [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Desenvolver com o Visual F# no Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio](install-visual-studio.md?view=vs-2017)
* [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Compilando assemblies lado a lado e aplicativos isolados do C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Idioma | Tópico |
|--------------|-----------|
| Visual Basic | [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2019) |
| Visual C# | [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2019) |
| Visual F# | [Desenvolver com o Visual F# no Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2019) |
| C++ | [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

* [Instalar o Visual Studio](install-visual-studio.md?view=vs-2019)
* [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-upgrade-visual-studio-projects-2019.md)
* [Compilando assemblies lado a lado e aplicativos isolados do C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end