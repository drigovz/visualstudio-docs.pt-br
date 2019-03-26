---
title: Estender diagramas de dependência
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 150621514f9153b1e9d67f8e9c85a00275c27b15
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416104"
---
# <a name="extend-dependency-diagrams"></a>Estender diagramas de dependência

Você pode escrever código para criar e atualizar diagramas de dependência e também para validar a estrutura do código do programa em relação a diagramas de dependência no Visual Studio. Você pode adicionar comandos que aparecem no menu de atalho (contexto) dos diagramas, personalizar gestos de arrastar e soltar e acessar o modelo de camada de modelos de texto. Você pode empacotar essas extensões em um Visual Studio Integration VSIX (extensão) e distribuí-los a outros usuários do Visual Studio.

 Para obter mais informações sobre diagramas de dependência, consulte:

-   [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)

-   [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)

-   [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)

-   [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)

##  <a name="prereqs"></a> Requisitos

Você deve ter os seguintes itens instalados no computador em que você deseja desenvolver suas extensões em camadas:

-   Visual Studio

-   [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)

-   SDK de modelagem para Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Você deve ter uma versão adequada do Visual Studio instalado no computador em que você deseja executar suas extensões em camadas.

Para ver quais versões do Visual Studio dão suporte a diagramas de dependência, consulte [suporte de versão para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-section"></a>Nesta seção
 [Adicionar comandos e gestos aos diagramas de dependência](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [Adicionar validação de arquitetura personalizada a diagramas de dependência](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [Adicionar propriedades personalizadas a diagramas de dependência](../modeling/add-custom-properties-to-layer-diagrams.md)

## <a name="see-also"></a>Consulte também

- [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)
- [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)
