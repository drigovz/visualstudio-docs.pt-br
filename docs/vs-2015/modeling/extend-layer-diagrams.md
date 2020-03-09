---
title: Estender diagramas de camada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409618"
---
# <a name="extend-layer-diagrams"></a>Estender diagramas de camada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode escrever código para criar e atualizar diagramas de camada e para validar a estrutura do código do programa em relação a diagramas de camada no Visual Studio. Você pode adicionar comandos que aparecem no menu de atalho (contexto) dos diagramas, personalizar gestos de arrastar e soltar e acessar o modelo de camada a partir de modelos de texto. Você pode empacotar essas extensões em uma extensão de integração do Visual Studio (VSIX) e distribuí-las a outros usuários do Visual Studio.

 Para obter mais informações sobre diagramas de camada, consulte:

- [Diagramas de camada: referência](../modeling/layer-diagrams-reference.md)

- [Diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md)

- [Criar diagramas de camada por meio de código](../modeling/create-layer-diagrams-from-your-code.md)

- [Validar o código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> Requisitos
 Você deve ter o seguinte instalado no computador em que deseja desenvolver suas extensões de camada:

- Visual Studio

- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)

- [SDK de modelagem para o Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148)

  Você deve ter uma versão adequada do Visual Studio instalada no computador em que deseja executar suas extensões de camada. Para obter mais informações, consulte [implantar uma extensão de modelo de camada](../modeling/deploy-a-layer-model-extension.md).

  Para ver quais versões do Visual Studio oferecem suporte a diagramas de camada, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Nesta seção
 [Adicionar comandos e gestos a diagramas de camada](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Adicionar validação de arquitetura personalizada a diagramas de camada](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Adicionar propriedades personalizadas a diagramas de camada](../modeling/add-custom-properties-to-layer-diagrams.md)

 [Navegar e atualizar modelos de camada no código do programa](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [Implantar uma extensão de modelo de camada](../modeling/deploy-a-layer-model-extension.md)

 [Solucionar problemas de extensões para diagramas de camada](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>Consulte Também
 [Definir e instalar um](../modeling/define-and-install-a-modeling-extension.md) [diagramas](../modeling/layer-diagrams-reference.md) de camada de extensão de modelagem: [diagramas de camada de referência: diretrizes](../modeling/layer-diagrams-guidelines.md) [crie diagramas de camada do código de](../modeling/create-layer-diagrams-from-your-code.md) [validação de código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md) [gere arquivos de um modelo UML](../modeling/generate-files-from-a-uml-model.md) [abra um modelo UML usando a API do Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
