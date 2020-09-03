---
title: Solucionar problemas de extensões para diagramas de camada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658469"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Solucionar problemas de extensões para diagramas de camada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico aborda alguns problemas que você pode encontrar ao criar extensões de modelo de camada.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-vsprvs"></a>Quando pressiono F5 para depurar minha extensão, meus comandos, manipuladores de gesto, extensões de validação ou propriedades personalizadas não aparecem em diagramas de camada na instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

1. Abra sua solução de extensão na instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e, no menu **Compilar** , clique em **Recompilar solução**.

2. Pressione **F5** ou **Ctrl + F5** para iniciar a instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Abra um diagrama de camada e teste sua extensão.

   Continue com o próximo procedimento, se necessário.

#### <a name="an-old-version-of-my-extension-runs"></a>Uma versão antiga da minha extensão é executada.

1. Certifique-se de que nenhuma instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] esteja em execução.

2. Exclua a seguinte pasta:%LocalAppData%\Microsoft\VisualStudio \\ [Version] \ComponentModelCache

   > [!NOTE]
   > % LocalAppData% normalmente é *driveName*: \Users \\ *username*\AppData\Local.

   Continue com o próximo procedimento, se necessário.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Uma versão antiga dos meus resultados de validação é exibida ou meu método de validação não é chamado.

1. Na instância experimental do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , no menu **Compilar** , clique em **limpar solução**. Isso limpa os resultados em cache da análise de validação anterior.

2. Verifique se as camadas em seu modelo estão associadas a elementos de código e se há pelo menos um link de dependência no modelo. A validação não será invocada se não houver nada a ser validado.

3. Os pontos de interrupção regulares podem não funcionar em um método de validação, pois são executados em um processo separado. Você deve inserir uma chamada para `System.Diagnostics.Debugger.Launch()` se desejar percorrer o método.

4. Em **Source. Extension. vsixmanifest** em seu projeto de validação de camada, certifique-se de ter adicionado um item de **componente do MEF** e um item de **tipo de extensão personalizada** sob **conteúdo**.

## <a name="see-also"></a>Consulte Também
 [Estender diagramas de camada](../modeling/extend-layer-diagrams.md)
