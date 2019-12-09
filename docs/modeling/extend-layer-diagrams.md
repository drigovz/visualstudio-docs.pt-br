---
title: Estender diagramas de dependência
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a8297ede4ce703c738133952bb13669ef6a6637
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645678"
---
# <a name="extend-dependency-diagrams"></a>Estender diagramas de dependência

Você pode escrever código para criar e atualizar diagramas de dependência e para validar a estrutura do código do programa em relação a diagramas de dependência no Visual Studio. Você pode adicionar comandos que aparecem no menu de atalho (contexto) dos diagramas, personalizar gestos de arrastar e soltar e acessar o modelo de camada a partir de modelos de texto. Você pode empacotar essas extensões em uma extensão de integração do Visual Studio (VSIX) e distribuí-las a outros usuários do Visual Studio.

## <a name="requirements"></a>Requisitos

Você deve ter o seguinte instalado no computador em que deseja desenvolver suas extensões de camada:

- Visual Studio

- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md)

- SDK de modelagem para Visual Studio

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Você deve ter uma edição adequada do Visual Studio instalada no computador em que deseja executar suas extensões de camada. Para ver quais edições do Visual Studio dão suporte a diagramas de dependência, consulte [suporte de edição para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="see-also"></a>Consulte também

- [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)
- [Diagramas de dependência: diretrizes](../modeling/layer-diagrams-guidelines.md)
- [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)
- [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)
