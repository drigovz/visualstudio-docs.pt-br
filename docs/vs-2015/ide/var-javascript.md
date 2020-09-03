---
title: '&lt;var&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <var> JavaScript XML tag
- var JavaScript XML tag
ms.assetid: 34ff9023-c81c-46d1-85b6-0022f0962e66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f72b403d4c6c9cc71bc2a3fdbff8f778a44b3b55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663068"
---
# <a name="ltvargt-javascript"></a>&lt;var&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações sobre a documentação para uma variável.

## <a name="syntax"></a>Sintaxe

```
<var type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    helpKeyword="keyword" locid="descriptionID">description
</var>
```

#### <a name="parameters"></a>Parâmetros
 `type` Opcional. O tipo de dados da variável. O tipo pode ser um dos seguintes:

- Um tipo de linguagem ECMAScript que está na especificação do ECMAScript 5, como `Number` e `Object`.

- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.

- Uma função de construtor JavaScript.

  `integer` Opcional. Se `type` for `Number`, especificará se a variável é um inteiro. Defina como `true` para indicar que a variável é um inteiro; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `domElement` Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se a variável documentada é um elemento DOM. Defina como `true` para especificar que a variável é um elemento DOM; caso contrário, defina como `false`. Se o atributo `type` não estiver definido e `domElement` estiver definido como `true`, o IntelliSense tratará a variável documentada como um `HTMLElement` ao executar o preenchimento de declaração.

  `mayBeNull` Opcional. Especifica se a variável documentada pode ser definida como null. Defina como `true` para indicar que a variável pode ser definida como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementType` Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.

  `elementInteger` Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementDomElement` Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.

  `elementMayBeNull` Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `helpKeyword` Opcional. A palavra-chave para Ajuda com F1.

  `locid` Opcional. O identificador de informações de localização sobre a variável. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo de identificador depende do formato especificado na [\<loc>](../ide/loc-javascript.md) marca.

  `description` Opcional. Uma descrição da variável.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir mostra como usar o elemento `<var>`.

```javascript
/// <var>A rectangle that has a width of 5.</var>
var Rectangle = {
    /// <field type = 'Number'>The width of the rectangle.</field>
    wid: 5,
    /// <field type = 'Number'>The length of the rectangle.</field>
    len: 0,
    /// <field type='Number'>Returns the area of the rectangle.</field>
    getArea: function (wid, len) {
        return len * wid;
    }
}
```

## <a name="see-also"></a>Consulte Também
 [Comentários de documentação XML](../ide/xml-documentation-comments-javascript.md)
