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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac74dde41a2d6cea0a768cfc89838cc34ce41afd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179320"
---
# <a name="ltvaluegt-javascript"></a>&lt;value&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações sobre a documentação para `get` e `set` funções para as propriedades do ECMAScript 3.  
  
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
 `type`  
 Opcional. O tipo de dados da propriedade. O tipo pode ser um dos seguintes:  
  
- Um tipo de linguagem ECMAScript que está na especificação do ECMAScript 5, como `Number` e `Object`.  
  
- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.  
  
- Uma função de construtor JavaScript.  
  
  `integer`  
  Opcional. Se `type` é `Number`, especifica se a propriedade é um inteiro. Definido como `true` para indicar que a propriedade é um inteiro; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `domElement`  
  Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se a propriedade documentada é um elemento DOM. Definido como `true` para especificar que a propriedade é um elemento DOM; caso contrário, defina como `false`. Se o `type` atributo não for definido e `domElement` é definido como `true`, IntelliSense trata a propriedade documentada como um `HTMLElement` ao executar o preenchimento de declaração.  
  
  `mayBeNull`  
  Opcional. Especifica se a propriedade documentada pode ser definida como null. Definido como `true` para indicar que a propriedade pode ser definida como nula; caso contrário, defina `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `elementType`  
  Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.  
  
  `elementInteger`  
  Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `elementDomElement`  
  Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.  
  
  `elementMayBeNull`  
  Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `locid`  
  Opcional. O identificador para obter informações sobre a propriedade de localização. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo do identificador depende do formato especificado no elemento [\<loc>](../ide/loc-javascript.md).  
  
  `description`  
  Opcional. Uma descrição da propriedade.  
  
## <a name="remarks"></a>Comentários  
 Uso de propriedades do ECMAScript 5 a [ \<resumo >](../ide/summary-javascript.md) elemento.  
  
 Use o `<value>` elemento imediatamente antes do `get` ou `set` função.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar o `<value>` elemento em um `get` função.  
  
```javascript  
function Sys$CancelEventArgs$get_cancel() {  
    /// <value type="Boolean" locid="P:J#Sys.CancelEventArgs.cancel"></value>  
    if (arguments.length !== 0) throw Error.parameterCount();  
    return this._cancel();  
}  
```  
  
## <a name="see-also"></a>Veja também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
