---
title: '&lt;value&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <value> JavaScript XML tag
- value JavaScript XML tag
ms.assetid: 983e31de-cb1d-411e-b60d-eea6698a26f6
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aefe710cc730d5624abc01bbdfc54d9961788787
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656392"
---
# <a name="ltvaluegt-javascript"></a>&lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações de documentação para funções de `get` e `set` para propriedades ECMAScript 3.

## <a name="syntax"></a>Sintaxe

```
<value type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID">description
</value>
```

#### <a name="parameters"></a>Parâmetros
 `type` Opcional. O tipo de dados da propriedade. O tipo pode ser um dos seguintes:

- Um tipo de linguagem ECMAScript que está na especificação do ECMAScript 5, como `Number` e `Object`.

- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.

- Uma função de construtor JavaScript.

  `integer` Opcional. Se `type` for `Number`, especifica se a propriedade é um número inteiro. Defina como `true` para indicar que a propriedade é um inteiro; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `domElement` Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se a propriedade documentada é um elemento DOM. Defina como `true` para especificar que a propriedade é um elemento DOM; caso contrário, defina como `false`. Se o atributo `type` não estiver definido e `domElement` estiver definido como `true`, o IntelliSense tratará a propriedade documentada como um `HTMLElement` ao executar a conclusão da instrução.

  `mayBeNull` Opcional. Especifica se a propriedade documentada pode ser definida como nula. Defina como `true` para indicar que a propriedade pode ser definida como nula; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementType` Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.

  `elementInteger` Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementDomElement` Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.

  `elementMayBeNull` Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `locid` Opcional. O identificador para informações de localização sobre a propriedade. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo do identificador depende do formato especificado no elemento [\<loc>](../ide/loc-javascript.md).

  `description` Opcional. Uma descrição da propriedade.

## <a name="remarks"></a>Comentários
 As propriedades ECMAScript 5 usam o elemento [\<summary >](../ide/summary-javascript.md) .

 Use o elemento `<value>` imediatamente antes da função `get` ou `set`.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir mostra como usar o elemento `<value>` em uma função `get`.

```javascript
function Sys$CancelEventArgs$get_cancel() {
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>
    if (arguments.length !== 0) throw Error.parameterCount();
    return this._cancel();
}
```

## <a name="see-also"></a>Veja também
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
