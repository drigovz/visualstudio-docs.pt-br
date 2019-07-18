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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 81a9a42a104adb2a9d9a9aba483e2588d7332868
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203533"
---
# <a name="ltreturnsgt-javascript"></a>&lt;returns&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações sobre a documentação para o resultado de uma chamada de método ou função.  
  
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
 `type`  
 Opcional. O tipo de dados do valor de retorno. O tipo pode ser um dos seguintes:  
  
- Digite uma linguagem ECMAScript na especificação do ECMAScript 5, como `Number` e `Object`.  
  
- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.  
  
- Uma função de construtor JavaScript.  
  
  `integer`  
  Opcional. Se `type` é `Number`, especifica se o valor de retorno é um inteiro. Definido como `true` para indicar que o valor de retorno é um inteiro; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `domElement`  
  Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se o valor de retorno documentado é um elemento DOM. Definido como `true` para especificar que o valor de retorno é um elemento DOM; caso contrário, defina como `false`. Se o `type` atributo não for definido e `domElement` é definido como `true`, IntelliSense trata o valor de retorno documentado como um `HTMLElement` ao executar o preenchimento de declaração.  
  
  `mayBeNull`  
  Opcional. Especifica se o documento retorna valor pode ser definido como null. Definido como `true` para indicar que o valor de retorno pode ser definido como nula; caso contrário, defina `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `elementType`  
  Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.  
  
  `elementInteger`  
  Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `elementDomElement`  
  Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.  
  
  `elementMayBeNull`  
  Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `locid`  
  Opcional. O identificador de informações de localização sobre o valor de retorno. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo do identificador depende do formato especificado na marca [\<loc>](../ide/loc-javascript.md).  
  
  `value`  
  Opcional. Especifica o código que deve ser avaliado para uso pelo IntelliSense em vez do código de função em si. Por exemplo, você pode usar esse atributo para fornecer o IntelliSense para retornos de chamada assíncronos, como um `Promise`. Usando o `value` do atributo com o `<returns>` elemento pode melhorar o desempenho de IntelliSense, ignorando a execução de código longo.  
  
  `description`  
  Opcional. Uma descrição do valor retornado.  
  
## <a name="remarks"></a>Comentários  
 O `<returns>` elemento deve ser colocado no corpo da função antes que as instruções.  
  
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
  
## <a name="see-also"></a>Veja também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
