---
title: Instalar versões do Visual Studio lado a lado
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: a2b77315363c404cd0647555e5a6ad21d36ac86b
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234985"
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

* Se você tentar usar o Visual Studio 2019 para abrir uma solução que foi criada no Visual Studio 2017 ou em uma versão anterior, talvez você precise alterar seus projetos e arquivos para que fiquem compatíveis com o Visual Studio 2019. Para obter mais informações, veja a página [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Se você desinstalar uma versão do Visual Studio em um computador que tem mais de uma versão instalada, as associações de arquivo do Visual Studio serão removidas para todas as versões.

* O Visual Studio não atualiza automaticamente extensões porque nem todas as extensões são compatíveis. Você deverá reinstalar as extensões do [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou do fornecedor de software.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Instale as versões secundárias do Visual Studio lado a lado

Ao atualizar de uma versão secundária do Visual Studio para a próxima, o instalador do Visual Studio atualizará sua instalação atual para a próxima versão nesse canal por padrão. Por exemplo, ao instalar a versão prévia do 16.6.4, o instalador tentará substituir a instalação atual do 16.6.3 preview, já que ambas as versões estão no canal de visualização 16,6. Isso ajuda a garantir que as versões mais antigas do Visual Studio não estejam ocupando espaço no seu computador. Em alguns casos específicos, pode ser útil instalar versões secundárias lado a lado. Em nosso exemplo, isso significa ter 16.6.3 e 16.6.4 no mesmo computador.

1. Baixe o [arquivo bootstrapper do Visual Studio](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) para a versão secundária que você deseja instalar lado a lado com suas versões existentes do Visual Studio.
2. Abra o prompt de comando no modo de administrador. Para fazer isso, abra o menu Iniciar do Windows, digite "cmd", clique com o botão direito do mouse no resultado da pesquisa do prompt de comando e selecione **Executar como administrador**. No prompt de comando, altere o diretório para a pasta onde o arquivo de bootstrapper do Visual Studio está localizado.
3. Execute o comando a seguir, especificando um novo caminho de pasta para o local de instalação e substituindo o nome do arquivo. exe pelo nome de bootstrapper apropriado para a versão do Visual Studio que você está instalando. O nome do arquivo. exe deve corresponder ou ser semelhante a um dos seguintes arquivos:
   * vs_community.exe para Visual Studio Community
   * vs_professional.exe para Visual Studio Professional
   * vs_enterprise.exe para Visual Studio Enterprise

```
vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
```
4. Siga as caixas de diálogo do instalador para selecionar os componentes necessários para a instalação. Para obter mais informações, consulte [instalar o Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versões do .NET Framework e instalações lado a lado

Os projetos Visual Basic, Visual C# e Visual F# usam a opção **Estrutura de Destino** no **Designer de Projeto** para especificar qual versão do .NET Framework um projeto usa. Para um projeto do C++, é possível alterar manualmente a estrutura de destino alterando o arquivo .vcxproj. Para obter mais informações, veja a página [Compatibilidade de versão no .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Ao criar um projeto, você pode especificar a qual versão do .NET Framework o projeto é direcionado na lista **.NET Framework** na caixa de diálogo **Novo Projeto**.

Para informações específicas do idioma, consulte o tópico apropriado na tabela a seguir.

::: moniker range="vs-2017"

| Linguagem | Tópico |
|--------------|-----------|
| Visual Basic | [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Desenvolver com o Visual F# no Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Confira também

* [Instalar o Visual Studio](install-visual-studio.md?view=vs-2017)
* [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [Como compilar assemblies lado a lado e aplicativos isolados do C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Linguagem | Tópico |
|--------------|-----------|
| Visual Basic | [Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Desenvolver com o Visual F# no Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Como: Modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Confira também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Portar, migrar e atualizar projetos do Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Como compilar assemblies lado a lado e aplicativos isolados do C/C++](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
