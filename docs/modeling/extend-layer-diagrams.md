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
ms.openlocfilehash: 9c164174b88ca9fdd815668084c1447e20de072c
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476563"
---
# <a name="extend-dependency-diagrams"></a>Estender diagramas de dependência

Você pode escrever código para criar e atualizar diagramas de dependência e validar a estrutura do código do programa em relação a diagramas de dependência no Visual Studio. Você pode adicionar comandos que aparecem no menu de atalho (contexto) dos diagramas, personalizar gestos de arrastar e soltar e acessar o modelo de camada de modelos de texto. Você pode empacotar essas extensões em um Visual Studio Integration VSIX (extensão) e distribuí-los a outros usuários do Visual Studio.

## <a name="requirements"></a>Requisitos

Você deve ter os seguintes itens instalados no computador em que você deseja desenvolver suas extensões em camadas:

- Visual Studio

- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)

- SDK de modelagem para Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Você deve ter uma edição adequada do Visual Studio instaladas no computador em que você deseja executar suas extensões em camadas. Para ver quais edições do Visual Studio dão suporte a diagramas de dependência, consulte [suporte de edição para a arquitetura e ferramentas de modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Consulte também

- [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)
- [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)
