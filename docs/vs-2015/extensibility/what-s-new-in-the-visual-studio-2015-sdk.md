---
title: O que há de novo no SDK do Visual Studio 2015 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6735f929f52387f4cb40406d6918894e72bb40d3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299681"
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Quais&#39;s novidades no SDK do Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O SDK do Visual Studio tem os seguintes recursos novos e atualizados para o Visual Studio 2015, o Visual Studio 2015 atualizado e o Visual Studio 2017.

## <a name="visual-studio-2017"></a>Visual Studio 2017

A partir do Visual Studio 2017, a verificação de modelos de projeto e item personalizados não será mais executada. Em vez disso, a extensão deve fornecer arquivos de manifesto de modelo que descrevem o local de instalação desses modelos. Você pode usar o Visual Studio 2017 para atualizar suas extensões VSIX. Se você implantar sua extensão usando um MSI, deverá gerar os arquivos de manifesto de modelo manualmente. Para obter mais informações, consulte [upgrading Custom Modelos de Projeto e Item para Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). O esquema de manifesto de modelo está documentado na [referência de esquema de manifesto de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="vs-2015-sdk-update-1"></a>Atualização 1 do SDK do VS 2015
 A atualização 1 inclui ferramentas para ajudar sua extensão a funcionar bem com temas de cores e o serviço de imagem do Visual Studio.

 Esses tópicos estão na seção [utilitários VSSDK](../extensibility/internals/vssdk-utilities.md) :

- As [ferramentas](../extensibility/internals/color-theming-tools.md) de ti de cores ajudam você a criar e Editar cores personalizadas para o Visual Studio.

- As [ferramentas de serviço de imagem](../extensibility/internals/image-service-tools.md) permitem trabalhar com arquivos de manifesto de imagem do Visual Studio.

## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nova maneira de adicionar o SDK do Visual Studio ao Visual Studio
 A partir do Visual Studio 2015, você não precisa baixar o SDK do Visual Studio separadamente. Em vez disso, você pode instalá-lo como parte do processo de instalação normal ou pode optar por instalá-lo mais tarde. Quando você abre ou cria uma solução VSIX, o Visual Studio solicitará que você instale o Ferramentas de Extensibilidade do Visual Studio. Para obter mais informações, consulte [instalando o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="new-ways-of-creating-extensions"></a>Novas maneiras de criar extensões
 A partir do SDK do Visual Studio 2015, você tem opções diferentes para criar extensões, dependendo da linguagem de programação que estiver usando.

### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic
 Para C# o e Visual Basic, há uma gama completa de modelos de item de projeto que permitem que você crie VSPackages, comandos de menu, janelas de ferramentas, classificadores de editor, adornos de editor e extensões de margem do editor. Você pode adicionar qualquer um deles ao projeto VSIX padrão. Para obter mais informações, consulte:

- [Criar uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- [Criar uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)

- [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- [Criar uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

     O assistente de VSPackage não cria mais extensões C# no ou Visual Basic.

### <a name="c"></a>C++
 Para C++o, o assistente de VSPackage dá suporte a comandos de menu, janelas de ferramentas e editores personalizados. Procure-o na caixa de diálogo **novo projeto** no  **C++ Visual/extensibilidade**.

## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblies de referência do SDK do VS via NuGet
 Para maior portabilidade e compartilhamento de projetos de extensibilidade, você pode usar as versões do NuGet dos assemblies de referência do SDK do VS.  Eles estão disponíveis no [NuGet.org](https://www.nuget.org/) publicado pelo [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) e podem ser facilmente adicionados ao seu projeto ou solução por meio da caixa de diálogo **referências/gerenciar pacotes NuGet** do Visual Studio. Você pode adicionar referências individuais a assemblies de extensibilidade específicos ou adicionar todos os assemblies de referências do SDK do VS ao mesmo tempo usando o [pacote meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)do SDK do vs. Para saber mais sobre o NuGet, consulte [visão geral do NuGet](https://docs.microsoft.com/nuget/) e [gerenciar pacotes NuGet usando a caixa de diálogo](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).

 Quando você usa as versões do NuGet dos assemblies de referência do SDK do VS, outro usuário não precisa instalar o SDK do VS para abrir e compilar seu projeto.  Os assemblies de referência do NuGet e as ferramentas de Build do SDK do VS serão instalados automaticamente no computador desse projeto.

 Os modelos de item do SDK do VS usam o NuGet para suas referências e ferramentas de compilação para que você obtenha os benefícios do NuGet por padrão.

> [!NOTE]
> Você pode continuar a usar os assemblies de referência instalados pelo SDK do VS com seus projetos (localizados em \<local de instalação do Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e projetos de extensibilidade existentes não precisam ser atualizados para usar pacotes NuGet.  A caixa de diálogo referências do projeto **/Adicionar referência** continua a usar os assemblies de referência instalados pelo SDK do vs.
>
> Se você quiser modificar seus projetos existentes para usar o NuGet, consulte [como migrar VSPackages para o Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) que tem uma seção sobre a atualização de projetos de extensibilidade para pacotes NuGet.

## <a name="light-bulbs"></a>Lâmpadas
 Uma das novas maneiras mais empolgantes de escrever código de extensão é fornecida pelo projeto Roslyn. Para obter mais informações, consulte [Roslyn](https://github.com/dotnet/Roslyn).

 Lâmpadas são um novo recurso que acompanha o VSSDK. Eles são ícones usados no editor do Visual Studio que se expandem para exibir um conjunto de ações de refatoração de código ou correções para problemas identificados pelos analisadores de código internos. Para obter mais informações, consulte [Walkthrough: exibindo sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).

## <a name="updated-user-experience-guidelines"></a>Diretrizes de experiência do usuário atualizadas
 Projetando novas extensões ou recursos para o Visual Studio? Confira as diretrizes de experiência do usuário atualizadas e expandidas do [Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Você encontrará os [tokens de cor](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamanhos de fonte](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), especificações de layout de [caixa de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e outras orientações necessárias para integrar perfeitamente sua nova interface do usuário com o Visual Studio.
