---
title: '&lt;field&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <field> JavaScript XML tag
- field JavaScript XML tag
ms.assetid: c494bae0-3095-42a3-aa0a-4c415188c65c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b2fe09070261460b7b83f54de44a07cf96d40cf2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181268"
---
# <a name="ltfieldgt-javascript"></a>&lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações sobre a documentação, incluindo uma descrição, para um campo ou um membro que é definido em um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<field name="fieldName" static="true|false"  
    type="FieldType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    helpKeyword="keyword" locid="descriptionID"  
    value="code">description  
</field>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `name`  
 O nome do campo ou membro. Quando o `<field>` elemento é usado em uma função de construtor, `name` é necessária e define o membro ao qual se aplica a marca. Quando o `<field>` elemento diretamente é anotar um campo, esse atributo é ignorado e o nome usado pelo Visual Studio é o nome do campo real no código-fonte.  
  
 `static`  
 Opcional. Especifica se o campo é um membro da função de construtor ou um membro do objeto retornado pela função de construtor. Definido como `true` para tratar o campo como um membro da função de construtor. Definido como `false` para tratar o campo como um membro do objeto retornado pela função de construtor.  
  
 `type`  
 Opcional. O tipo de dados do campo. O tipo pode ser um dos seguintes:  
  
- Digite uma linguagem ECMAScript na especificação do ECMAScript 5, como `Number` e `Object`.  
  
- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.  
  
- Uma função de construtor JavaScript.  
  
  `integer`  
  Opcional. Se `type` é `Number`, especifica se o campo é um inteiro. Definido como `true` para indicar que o campo é um inteiro; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `domElement`  
  Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se o campo documentado é um elemento DOM. Definido como `true` para especificar que o campo é um elemento DOM; caso contrário, defina como `false`. Se o `type` atributo não for definido e `domElement` é definido como `true`, IntelliSense trata o campo documentado como um `HTMLElement` ao executar o preenchimento de declaração.  
  
  `mayBeNull`  
  Opcional. Especifica se o campo documentado pode ser definido como null. Definido como `true` para indicar que o campo pode ser definido como nulo; caso contrário, defina `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `elementType`  
  Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.  
  
  `elementInteger`  
  Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `elementDomElement`  
  Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.  
  
  `elementMayBeNull`  
  Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.  
  
  `helpKeyword`  
  Opcional. A palavra-chave para a ajuda F1.  
  
  `locid`  
  Opcional. O identificador para obter informações sobre o campo de localização. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo do identificador depende do formato especificado na marca [\<loc>](../ide/loc-javascript.md).  
  
  `value`  
  Opcional. Especifica o código que deve ser avaliado para uso pelo IntelliSense em vez do código de função em si. Para `<field>`, este atributo tem suporte para funções de construtor, mas não há suporte para literais de objeto. Você pode usar esse atributo é fornecer informações de tipo quando o tipo de campo é indefinido. Por exemplo, você pode usar `value=’1’` para tratar o tipo de campo como um número.  
  
  `description`  
  Opcional. Uma descrição para o campo.  
  
## <a name="remarks"></a>Comentários  
 O `name` atributo é necessário quando você está documentando um campo em uma função de construtor. Para todos os outros cenários, todos os atributos para o `<field>` elemento são opcionais.  
  
 Quando você estiver documentando uma função de construtor, o `<field>` elemento deve aparecer imediatamente antes da declaração do campo. O `name` atributo deve corresponder ao nome de campo que é usado no código-fonte. Para membros do objeto, o `name` atributo poderá ser omitido se o `<field>` elemento aparece imediatamente antes da declaração de membro de objeto.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar o elemento `<field>`.  
  
```javascript  
// Use of <field> in an object definition.  
var Rectangle = {  
    /// <field type='Number'>The width of the rectangle.</field>  
    wid: 5,  
    /// <field type='Number'>The length of the rectangle.</field>  
    len: 0,  
    /// <field type='Number'>Returns the area of the rectangle.</field>  
    getArea: function (wid, len) {  
        return len * wid;  
    }  
}  
  
// Use of <field> in a constructor function.  
// The name attribute is required.  
function Engine() {  
    /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
    this.HorsePower = 150;  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<field>` elemento com o `static` atributo definido como `true`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
// IntelliSense on the field is available here.  
Engine.  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<field>` elemento com o `static` atributo definido como `false`.  
  
```javascript  
function Engine() {  
    /// <field name='HorsePower' static='false' type='Number'>Non-static field desc.</field>  
}  
  
Engine.HorsePower = 140;  
var eng = new Engine();  
// IntelliSense on the field is available here.  
eng.  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<field>` elemento com o `value` atributo.  
  
```javascript  
function calculator(a) {  
    /// <field name='f' value='1'/>  
}  
new calculator().f.   // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Veja também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
