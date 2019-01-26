---
title: Sintaxe do caminho de domínio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: b8825d123c9d4cce5b72582fe213ba61ce6e7f6b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975953"
---
# <a name="domain-path-syntax"></a>Sintaxe do caminho de domínio
As definições de DSL usam uma sintaxe semelhante a XPath para localizar elementos específicos em um modelo.

 Normalmente, não é necessário trabalhar com essa sintaxe diretamente. Caso ela aparecer na janela Detalhes de DSL ou Propriedades, você pode clicar na seta para baixo e usar o editor de caminho. No entanto, o caminho aparecerá nesta forma no campo depois de você ter usado o editor.

 Um caminho de domínio tem a seguinte forma:

 *RelationshipName.PropertyName/!Role*

 ![Referência CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 A sintaxe percorre a árvore do modelo. Por exemplo, a relação de domínio **CommentReferencesSubjects** na ilustração acima tem um **assuntos** função. O segmento de caminho **/! Subjectt** Especifica que o caminho termina em elementos acessados por meio de **assuntos** função.

 Cada segmento inicia com o nome de uma relação de domínio. Se a passagem for de um elemento em uma relação, o segmento de caminho aparecerá como *Relationship*. Se o salto for de um link para um elemento, o segmento de caminho é exibido como *relação /! RoleName*.

 Barras separam a sintaxe de um caminho. Cada segmento de caminho é um salto de um elemento para um link (uma instância de uma relação) ou de um link para um elemento. Os segmentos de caminho normalmente aparecem em pares. Um segmento de caminho representa um salto de um elemento para um link e o próximo segmento representa um salto do link para o elemento na outra extremidade. (Qualquer link também pode ser a origem ou destino de uma relação).

 O nome que você usa para o salto do elemento ao link é o valor de `Property Name` da função. O nome que você usa para o salto do link ao elemento é o nome da função de destino.

## <a name="see-also"></a>Consulte também

- [Noções básicas sobre modelos, classes e relações](../modeling/understanding-models-classes-and-relationships.md)