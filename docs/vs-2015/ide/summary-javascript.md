---
title: '&lt;summary&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- summary JavaScript XML tag
- <summary> JavaScript XML tag
ms.assetid: 6540582d-bdb3-42ec-ad2f-c176783e6f9c
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f283c2c1825c4b8b02fb5b044ce113231a919317
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646842"
---
# <a name="ltsummarygt-javascript"></a>&lt;summary&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica a descrição de uma função ou um método.

## <a name="syntax"></a>Sintaxe

```
<summary locid="descriptionID">description
</summary>
```

#### <a name="parameters"></a>Parâmetros
 `locid` Opcional. O identificador de informações de localização sobre o método ou função. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo do identificador depende do formato especificado no elemento [\<loc>](../ide/loc-javascript.md).

 `description` Opcional. Uma descrição da função ou do método.

## <a name="remarks"></a>Comentários
 Os elementos usados para anotar as funções, que incluem [\<summary>](../ide/summary-javascript.md), [\<param>](../ide/param-javascript.md) e [\<returns>](../ide/returns-javascript.md), precisam ser colocados no corpo da função antes de quaisquer instruções.

## <a name="example"></a>Exemplo
 O código a seguir mostra como usar o elemento `<summary>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when supplied a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

```

## <a name="see-also"></a>Veja também
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
