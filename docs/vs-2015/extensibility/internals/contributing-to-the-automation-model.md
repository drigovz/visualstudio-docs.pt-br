---
title: Contribuindo para o modelo de automação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c84ea078f9b7c1268b765111cc400f6e51b783f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196989"
---
# <a name="contributing-to-the-automation-model"></a>Contribuindo com o modelo de automação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O Visual Studio fornece um conjunto de interfaces de automação para personalizar o ambiente. O modelo de automação é o modelo de objeto que permite que os usuários finais criem suplementos e extensões do Visual Studio.  
  
 Além disso, é apropriado para você, como desenvolvedor VSPackage, para contribuir com o modelo de automação; ao fazer isso, você permite que os usuários finais do seu VSPackage criem suplementos e geralmente fornecem uma experiência de modelo de usuário consistente quando usam o VSPackage no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 Para tornar a experiência do usuário final consistente, você pode seguir um conjunto de diretrizes ao projetar seu VSPackage para que o modelo de automação para seu VSPackage siga as ideias em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)  
 Define o modelo de automação como um grupo de objetos relacionados que controlam as principais facetas do ambiente comum. Esse conjunto de objetos é mostrado em um diagrama do modelo de automação.  
  
 [Fornecendo automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)  
 Discute as duas maneiras principais de fornecer automação para seu VSPackage.  
  
 [Expondo objetos do projeto](../../extensibility/internals/exposing-project-objects.md)  
 Fornece instruções passo a passo para a criação de objetos específicos do VSPackage.  
  
 [Modelagem do projeto](../../extensibility/internals/project-modeling.md)  
 Explica os objetos de projeto padrão que são necessários para criar a automação para o novo tipo de projeto e ilustra o caminho que a automação de projeto segue. Este tópico também fornece listagens de declarações e implementação para classes.  
  
 [Expondo eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 Fornece instruções passo a passo para a criação de eventos para seu modelo de automação.  
  
 [Suporte à automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)  
 Descreve como retornar um objeto Automation para dar suporte a propriedades de uma caixa de diálogo de **Opções** personalizadas do VSPackage no menu de **ferramentas** , estendendo o `DTE.Properties` objeto.  
  
 [Fornecendo automação de código](../../extensibility/internals/providing-automation-for-code.md)  
 Explica que a criação de um modelo de automação para seu código não é necessária. No entanto, um link é fornecido neste tópico que fornece informações criteriosas sobre modelos de código.  
  
 [Como fornecer automação para o Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 Explica que fornecer automação é uma boa ideia sempre que você deseja disponibilizar objetos de automação em uma janela, e o ambiente ainda não fornece um objeto de automação pronto. Discute a automação para janelas de ferramentas e janelas de documentos.  
  
 [Usando o modelo de automação](../../extensibility/internals/using-the-automation-model.md)  
 Fornece dois exemplos de código que mostram como um consumidor de automação Obtém os objetos de automação de projeto iniciais.  
  
 [Automação de configuração e objetos SelectedItem](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 Fornece informações sobre automação para opções de configuração e automação para itens selecionados.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 Fornece um exemplo de código que mostra como um VSPackage participa do modelo de objeto de automação do DTE. Lista os parâmetros, valores de retorno e comentários selecionados.  
  
## <a name="related-sections"></a>Seções relacionadas
