---
title: '&lt;returns&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8fd8cdc8acdbf42b97e00f3c85647dd863721d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669961"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações de documentação para o resultado de uma chamada de função ou método.

## <a name="syntax"></a>Sintaxe

```
<returns type="ValueType" integer="true|false"
    domElement="true|false" mayBeNull="true|false"
    elementType="ArrayElementType" elementInteger="true|false"
    elementDomElement="true|false" elementMayBeNull="true|false"
    locid="descriptionID" value="code">description
</returns>
```

#### <a name="parameters"></a>Parâmetros
 `type` Opcional. O tipo de dados do valor de retorno. O tipo pode ser um dos seguintes:

- Um tipo de linguagem ECMAScript na especificação ECMAScript 5, como `Number` e `Object` .

- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.

- Uma função de construtor JavaScript.

  `integer` Opcional. Se `type` for `Number` , especifica se o valor de retorno é um inteiro. Defina como `true` para indicar que o valor de retorno é um inteiro; caso contrário, defina como `false` . Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `domElement` Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se o valor de retorno documentado é um elemento DOM. Defina como `true` para especificar que o valor de retorno é um elemento DOM; caso contrário, defina como `false` . Se o `type` atributo não estiver definido e `domElement` for definido como `true` , o IntelliSense tratará o valor de retorno documentado como um `HTMLElement` ao executar a conclusão da instrução.

  `mayBeNull` Opcional. Especifica se o valor de retorno documentado pode ser definido como nulo. Defina como `true` para indicar que o valor de retorno pode ser definido como nulo; caso contrário, defina como `false` . O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementType` Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.

  `elementInteger` Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementDomElement` Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.

  `elementMayBeNull` Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `locid` Opcional. O identificador para informações de localização sobre o valor de retorno. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo de identificador depende do formato especificado na [\<loc>](../ide/loc-javascript.md) marca.

  `value` Opcional. Especifica o código que deve ser avaliado para uso pelo IntelliSense em vez do próprio código de função. Por exemplo, você pode usar esse atributo para fornecer IntelliSense para retornos de chamada assíncronos, como um `Promise` . O uso do `value` atributo com o `<returns>` elemento pode melhorar o desempenho do IntelliSense, ignorando a execução de código demorado.

  `description` Opcional. Uma descrição do valor retornado.

## <a name="remarks"></a>Comentários
 O `<returns>` elemento deve ser colocado no corpo da função antes de qualquer instrução.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir mostra como usar o elemento `<returns>`.

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

// The following examples use the <remarks> element with a value attribute.

function getJson(complete) {
    /// <returns value='complete("")' ></returns>
    var r = new XMLHttpRequest();
    // . . .
}

getJson(function (json) {
    json.  // IntelliSense for a String object is
           // available here.
});

function calculate(x) {
    /// <returns value='1'/>
}
calculate().  // Completion list for a Number.

```

## <a name="see-also"></a>Consulte Também
 [Comentários de documentação XML](../ide/xml-documentation-comments-javascript.md)
