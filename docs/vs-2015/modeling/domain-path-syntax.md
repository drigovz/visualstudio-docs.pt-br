---
title: Sintaxe do caminho de domínio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b25b47b5b711f09334501ed21abf06cb66402b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669734"
---
# <a name="domain-path-syntax"></a>Sintaxe do caminho de domínio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As definições de DSL usam uma sintaxe semelhante a XPath para localizar elementos específicos em um modelo.

 Normalmente, não é necessário trabalhar com essa sintaxe diretamente. Caso ela aparecer na janela Detalhes de DSL ou Propriedades, você pode clicar na seta para baixo e usar o editor de caminho. No entanto, o caminho aparecerá nesta forma no campo depois de você ter usado o editor.

 Um caminho de domínio tem a seguinte forma:

 *RelationshipName. PropertyName/! Cargo*

 ![Relação de referência de CommentReferencesSubjects](../modeling/media/dsl-reference.png "dsl_reference")

 A sintaxe percorre a árvore do modelo. Por exemplo, a relação de domínio **CommentReferencesSubjects** na ilustração acima tem uma função **Subjects** . O segmento de caminho **/! Subject** especifica que o caminho termina em elementos acessados por meio da função **Subjects** .

 Cada segmento inicia com o nome de uma relação de domínio. Se a passagem for de um elemento para uma relação, o segmento de caminho aparecerá como *relationship. PropertyName*. Se o salto for de um link para um elemento, o segmento de caminho aparecerá como *relationship/! RoleName*.

 Barras separam a sintaxe de um caminho. Cada segmento de caminho é um salto de um elemento para um link (uma instância de uma relação) ou de um link para um elemento. Os segmentos de caminho normalmente aparecem em pares. Um segmento de caminho representa um salto de um elemento para um link e o próximo segmento representa um salto do link para o elemento na outra extremidade. (Qualquer link também pode ser a origem ou destino de uma relação).

 O nome que você usa para o salto do elemento ao link é o valor de `Property Name` da função. O nome que você usa para o salto do link ao elemento é o nome da função de destino.

## <a name="see-also"></a>Consulte também
 [Noções básicas sobre modelos, classes e relações](../modeling/understanding-models-classes-and-relationships.md)
