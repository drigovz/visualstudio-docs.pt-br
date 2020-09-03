---
title: Solução de problemas com erros de direcionamento do .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1c496fd457e80220bb2ea4a2f032cef9508d9dcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631595"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Solução de problemas de erros de definição de destino do .NET Framework

Este tópico descreve os erros do MSBuild que podem ocorrer devido a referência problemas e como você pode resolver esses erros.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Você fez referência a um projeto ou assembly direcionado a uma versão diferente do .NET Framework

 É possível criar aplicativos que referenciam projetos ou assemblies direcionados a outras versões do .NET Framework. Por exemplo, você pode criar um aplicativo direcionado ao perfil de cliente do .NET Framework 4, mas que referencia um assembly direcionado ao .NET Framework 2.0. Entretanto, se você criar um projeto direcionado a uma versão anterior do .NET Framework, você não poderá definir uma referência nesse projeto a um projeto ou um assembly direcionado ao perfil de cliente para o .NET Framework 4 ou ao próprio .NET Framework 4. Para resolver o erro, certifique-se de que seu aplicativo seja direcionado a um perfil ou a perfis compatíveis com o perfil que é o destino dos projetos ou assemblies referenciados pelo seu aplicativo.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Você novamente direcionou um projeto para uma versão diferente do .NET Framework

 Se você alterar a versão de destino do .NET Framework de seu aplicativo, o Visual Studio alterará algumas das referências, mas você poderá precisar atualizar algumas referências manualmente. Por exemplo, um dos erros mencionados anteriormente pode ocorrer se você alterar um aplicativo para o .NET Framework 3,5 Service Pack 1 e esse aplicativo tiver recursos ou configurações que dependem do perfil do cliente para o .NET Framework 4.

 Para contornar as configurações do aplicativo, abra o **Gerenciador de Soluções**, escolha **Mostrar Todos os Arquivos** e edite o arquivo *app.config* no editor de XML do Visual Studio. Altere a versão nas configurações para coincidir com a versão apropriada do .NET Framework. Por exemplo, você pode alterar a configuração de versão de 4.0.0.0 para 2.0.0.0. Da mesma forma, para um aplicativo que tenha adicionado recursos, abra o **Gerenciador de Soluções**, escolha o botão **Mostrar Todos os Arquivos**, expanda **Meu Projeto** (Visual Basic) ou **Propriedades** (C#) e, em seguida, edite o arquivo *Resources.resx* no editor XML do Visual Studio. Altere a configuração de versão de 4.0.0.0 para 2.0.0.0.

 Se seu aplicativo tiver recursos como ícones ou bitmaps ou configurações, como cadeias de conexão de dados, você também pode resolver o erro, removendo todos os itens na página **Configurações** do **Project Designer** e, em seguida, adicionando novamente as configurações necessárias.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Você redirecionou um projeto para uma versão diferente do .NET Framework e as referências não são resolvidas

 Se você redirecionar um projeto para uma versão diferente do .NET Framework, as referências poderão não ser resolvidas corretamente em alguns casos. Explícitas referências totalmente qualificadas para assemblies geralmente causam esse problema, mas você pode resolvê-lo removendo as referências que não são resolvidas e, em seguida, adicioná-los ao projeto. Como alternativa, você pode editar o arquivo de projeto para substituir as referências. Primeiro, você pode remover referências da seguinte forma:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Em seguida, substitua-os pelo seguinte formato:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Depois de fechar e reabrir o projeto, você também deve recompilá-lo para garantir que todas as referências resolver corretamente.

## <a name="see-also"></a>Confira também

- [Como definir uma versão do .NET Framework como destino](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework perfil do cliente](/dotnet/framework/deployment/client-profile)
- [Visão geral do direcionamento de estrutura](../ide/visual-studio-multi-targeting-overview.md)
- [Multidirecionamento](../msbuild/msbuild-multitargeting-overview.md)
