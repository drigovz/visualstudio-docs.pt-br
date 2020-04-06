---
title: Contribuindo para o Modelo de Automação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709263"
---
# <a name="contribute-to-the-automation-model"></a>Contribua para o modelo de automação
O Visual Studio fornece um conjunto de interfaces de automação para personalizar o ambiente. O modelo de automação é o modelo de objeto que permite que os usuários finais criem complementos e extensões do Visual Studio.

 Além disso, é apropriado para você, como desenvolvedor de VSPackage, contribuir para o modelo de automação; ao fazer isso, você habilita os usuários finais do seu VSPackage para criar complementos e geralmente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornecer uma experiência consistente de modelo de usuário quando eles usam o seu VSPackage em .

 Para tornar a experiência do usuário final consistente, você pode seguir um conjunto de diretrizes ao projetar seu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage para que o modelo de automação do seu VSPackage siga as idéias em .

## <a name="in-this-section"></a>Nesta seção
- [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)

 Define o modelo de automação como um grupo relacionado de objetos que controlam as principais facetas do ambiente comum. Este conjunto de objetos é retratado em um diagrama do modelo de automação.

- [Fornecer automação para VSPackages](../../extensibility/internals/providing-automation-for-vspackages.md)

 Discute as duas principais maneiras de fornecer automação para o seu VSPackage.

- [Expor objetos do projeto](../../extensibility/internals/exposing-project-objects.md)

 Fornece instruções passo-a-passo para criar objetos específicos do VSPackage.

- [Modelagem de projetos](../../extensibility/internals/project-modeling.md)

 Explica os objetos de projeto padrão necessários para criar automação para o seu novo tipo de projeto e ilustra o caminho que a automação do projeto segue. Este tópico também fornece listas de declarações e implementação para classes.

- [Expor eventos](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 Fornece instruções passo a passo para criar eventos para o seu modelo de automação.

- [Suporte à automação para páginas de opções](../../extensibility/internals/automation-support-for-options-pages.md)

 Descreve como devolver um objeto de automação para suportar propriedades da caixa de diálogo **Opções personalizadas** do VSPackage no menu **Ferramenta,** estendendo o `DTE.Properties` objeto.

- [Fornecer automação para código](../../extensibility/internals/providing-automation-for-code.md)

 Explica que a criação de um modelo de automação para o seu código não é necessária. No entanto, um link é fornecido neste tópico que fornece informações perspicazes em modelos de código.

- [Como: Fornecer automação para Windows](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 Explica que fornecer automação é uma boa ideia sempre que você quiser disponibilizar objetos de automação em uma janela, e o ambiente ainda não fornece um objeto de automação pronto. Discute automação para janelas de ferramentas e janelas de documentos.

- [Use o modelo de automação](../../extensibility/internals/using-the-automation-model.md)

 Fornece dois exemplos de código que mostram como um consumidor de automação obtém os objetos iniciais de automação do projeto.

- [Automação para configuração e objetos selecionados](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 Fornece informações sobre automação para objetos de configuração e itens selecionados.

## <a name="reference"></a>Referência
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>Fornece uma amostra de código que mostra como um VSPackage participa do modelo de objeto de automação DTE. Lista parâmetros, valores de retorno e observações selecionadas.
