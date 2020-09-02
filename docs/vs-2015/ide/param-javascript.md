---
title: '&lt;param&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <param> JavaScript XML tag
- param JavaScript XML tag
ms.assetid: 2c4e0167-c1dd-4e54-83f1-c437856bddc1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca6207d22d82e607fa589f944230b36b46e633c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670356"
---
# <a name="ltparamgt-javascript"></a>&lt;param&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações de documentação para um parâmetro em uma função ou método.

## <a name="syntax"></a>Sintaxe

```
<param name="parameterName" type="ParameterType"
    integer="true|false" domElement="true|false"
    mayBeNull="true|false" elementType="ArrayElementType"
    elementInteger="true|false" elementDomElement="true|false"
    elementMayBeNull="true|false" locid="descriptionID"
    parameterArray="true|false" optional="true|false"
    value="code">description
</param>
```

#### <a name="parameters"></a>Parâmetros
 `name` Necessário. O nome do parâmetro.

 `type` Opcional. O tipo de dados do parâmetro. O tipo pode ser um dos seguintes:

- Um tipo de linguagem ECMAScript na especificação ECMAScript 5, como `Number` e `Object` .

- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.

- Uma função de construtor JavaScript.

  `integer` Opcional. Se `type` for `Number` , especifica se o parâmetro é um inteiro. Defina como `true` para indicar que o parâmetro é um inteiro; caso contrário, defina como `false` . Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `domElement` Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se o parâmetro documentado é um elemento DOM. Defina como `true` para especificar que o parâmetro é um elemento DOM; caso contrário, defina como `false` . Se o `type` atributo não estiver definido e `domElement` for definido como `true` , o IntelliSense tratará o parâmetro documentado como um `HTMLElement` ao executar a conclusão da instrução.

  `mayBeNull` Opcional. Especifica se o parâmetro documentado pode ser definido como nulo. Defina como `true` para indicar que o parâmetro pode ser definido como nulo; caso contrário, defina como `false` . O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementType` Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.

  `elementInteger` Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementDomElement` Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.

  `elementMayBeNull` Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `locid` Opcional. O identificador para informações de localização sobre o parâmetro. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo de identificador depende do formato especificado no [\<loc>](../ide/loc-javascript.md) elemento.

  `parameterArray` Opcional. Especifica se o parâmetro documentado pode ser repetido na chamada de função, semelhante a parâmetros repetidos com suporte na `String.format` função. Defina como `true` para indicar que o parâmetro pode ser repetido; caso contrário, defina como `false` . Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `optional` Opcional. Especifica se o parâmetro documentado é opcional na função de chamada. Defina como `true` para indicar que o parâmetro é opcional; caso contrário, defina como `false` .

  `value` Opcional. Especifica o código que deve ser avaliado para uso pelo IntelliSense em vez do próprio código de função. Você pode usar esse atributo para fornecer informações de tipo quando o tipo de parâmetro é indefinido. Por exemplo, você pode usar `value=’1’` para tratar o tipo de parâmetro como um número.

  `description` Opcional. Uma descrição do parâmetro.

## <a name="remarks"></a>Comentários
 O único atributo necessário é `name` . Todos os outros atributos são opcionais.

 Elementos usados para anotar funções, como, [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) e [\<returns>](../ide/returns-javascript.md) , devem ser colocados no corpo da função antes de qualquer instrução.

 Se houver vários `<param>` elementos que têm o mesmo nome, um dos `<param>` elementos será usado e os elementos redundantes serão ignorados. O comportamento que determina qual elemento é usado não está definido. Se se `name` referir a um parâmetro inexistente, o elemento será ignorado.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir mostra como usar o elemento `<param>`.

```javascript
function areaFunction(radiusParam)
{
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>
    /// <returns type="Number">The area.</returns>
    var areaVal;
    areaVal = Math.PI * radiusParam * radiusParam;
    return areaVal;
}

// Uses of <param> with the value attribute.

function calculate(a) {
    /// <param name='a' value='1'/>
    a.    // Completion list for a Number.
}

function calculate(a) {
    /// <param name='a' value='{x:0,y:0}'/>
    a.    // x and y appear in the completion list.
}

```

## <a name="see-also"></a>Consulte Também
 [Comentários de documentação XML](../ide/xml-documentation-comments-javascript.md)
