---
title: 'Como: migrar projetos de extensibilidade para o Visual Studio 2015 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2f4926a503304491164635b983353ba7f3bb0f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75915978"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Como migrar projetos de extensibilidade para o Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veja como atualizar sua extensão.  
  
> [!IMPORTANT]
> Se você pretende manter uma versão de sua solução de extensão para uma versão anterior do Visual Studio, certifique-se de fazer uma cópia antes de atualizá-la. Pode ser difícil retornar a versão atualizada para seu estado anterior.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Para atualizar uma solução de extensibilidade  
  
1. Usando a cópia que você deseja atualizar, abra-a na nova versão. Você será avisado de que a atualização não é reversível.  
  
2. Após a conclusão da atualização, altere o caminho do programa externo para a nova versão do devenv.exe. Clique com o botão direito do mouse no nó do projeto na **Gerenciador de soluções**e escolha **Propriedades**. Na guia **depurar** , localize a caixa de texto por **Iniciar programa externo** e altere o caminho de devenv.exe para o caminho do Visual Studio 2015, que deve ser semelhante ao seguinte:  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3. Adicione uma referência a Microsoft.VisualStudio.Shell.14.0.dll. (Clique com o botão direito do mouse no nó do projeto na **Gerenciador de soluções** e escolha **Adicionar/referência**. Selecione a guia **extensões** e, em seguida, verifique **Microsoft. VisualStudio. Shell. 14.0**.)  
  
4. Compile a solução. Os arquivos criados são implantados em:  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions \\<nome do autor \> \\<nome do projeto \> \\<\> \\ versão do projeto**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Para atualizar um projeto de extensibilidade para assemblies de referência do SDK do NuGet VS  
  
1. Determine os assemblies de referência do SDK do VS que seu projeto precisa.  Em **Gerenciador de soluções**, expanda o nó **referências** do projeto e examine a lista de referências do projeto.  O SDK do VS referencia assemblies terá o prefixo **Microsoft. VisualStudio** no nome (por exemplo: Microsoft. VisualStudio. Shell. 14.0).  
  
2. Remova os assemblies de referência do SDK do VS do projeto selecionando-os, clique com o botão direito do mouse e **remova**.  
  
3. Adicione as versões do NuGet dos assemblies de referência do SDK do VS.  Ainda no nó **referências do Gerenciador de soluções** , abra o **gerenciar pacotes NuGet..** . .  Se você quiser saber mais sobre essa caixa de diálogo, consulte [gerenciar pacotes NuGet usando a caixa de diálogo](/nuget/consume-packages/install-use-packages-visual-studio). Os assemblies de referência do SDK do VS são publicados em [NuGet.org](https://www.nuget.org/) por [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4. Usando o **NuGet.org** como a **origem do pacote**, procure o nome do pacote NuGet que corresponde ao assembly de referência desejado (por exemplo: Microsoft. VisualStudio. Shell. 14.0) e instale-o em seu projeto.  O NuGet pode adicionar vários assemblies de referência para atender às dependências do assembly inicial.  
  
     Se preferir, você pode adicionar todos os assemblies de referência do SDK do VS de uma só vez instalando o [pacote meta](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)do SDK do vs.  
  
5. Você também pode alternar para o uso da versão NuGet das ferramentas de Build do SDK do VS. Este pacote NuGet é [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e, uma vez adicionado ao seu projeto, incluirá as ferramentas necessárias e os arquivos de destino para permitir que você crie seu projeto de extensibilidade em um computador sem o SDK do vs instalado.  
  
> [!NOTE]
> Não é necessário que você atualize seus projetos de extensibilidade existentes para usar as ferramentas e os assemblies de referência do NuGet.  Eles podem continuar a criar usando assemblies de referência e ferramentas instaladas com o SDK do VS.
