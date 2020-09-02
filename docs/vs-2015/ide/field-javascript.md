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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3fc786e4d99d1eaff4a8b152ea9496ce8400ff1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663853"
---
# <a name="ltfieldgt-javascript"></a>&lt;field&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica informações de documentação, incluindo uma descrição, para um campo ou membro definido em um objeto.

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
 `name` O nome do campo ou membro. Quando o `<field>` elemento é usado em uma função de construtor, `name` é necessário e define o membro ao qual a marca se aplica. Quando o `<field>` elemento está anotando diretamente um campo, esse atributo é ignorado e o nome usado pelo Visual Studio é o nome do campo real no código-fonte.

 `static` Opcional. Especifica se o campo é um membro da função de construtor ou um membro do objeto retornado pela função de construtor. Defina como `true` para tratar o campo como um membro da função de construtor. Defina como `false` para tratar o campo como um membro do objeto retornado pela função de construtor.

 `type` Opcional. O tipo de dados do campo. O tipo pode ser um dos seguintes:

- Um tipo de linguagem ECMAScript na especificação ECMAScript 5, como `Number` e `Object` .

- Um objeto DOM, como `HTMLElement`, `Window` e `Document`.

- Uma função de construtor JavaScript.

  `integer` Opcional. Se `type` for `Number` , especifica se o campo é um inteiro. Defina como `true` para indicar que o campo é um inteiro; caso contrário, defina como `false` . Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `domElement` Opcional. Esse atributo foi preterido; o atributo `type` tem precedência sobre esse atributo. Esse atributo especifica se o campo documentado é um elemento DOM. Defina como `true` para especificar que o campo é um elemento DOM; caso contrário, defina como `false` . Se o `type` atributo não estiver definido e `domElement` for definido como `true` , o IntelliSense tratará o campo documentado como um `HTMLElement` ao executar a conclusão da instrução.

  `mayBeNull` Opcional. Especifica se o campo documentado pode ser definido como nulo. Defina como `true` para indicar que o campo pode ser definido como nulo; caso contrário, defina como `false` . O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementType` Opcional. Se `type` for `Array`, esse atributo especificará o tipo dos elementos na matriz.

  `elementInteger` Opcional. Se `type` for `Array` e `elementType` for `Number`, este atributo especificará se os elementos na matriz são inteiros. Defina como `true` para indicar que os elementos na matriz são inteiros; caso contrário, defina como `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `elementDomElement` Opcional. Esse atributo foi preterido; o atributo `elementType` tem precedência sobre esse atributo. Se `type` for `Array`, este atributo especificará se os elementos na matriz são elementos DOM. Defina como `true` para especificar que os elementos são elementos DOM; caso contrário, defina como `false`. Se o atributo `elementType` não estiver definido e `elementDomElement` estiver definido como `true`, o IntelliSense tratará cada elemento na matriz como um `HTMLElement` ao executar o preenchimento de declaração.

  `elementMayBeNull` Opcional. Se `type` for `Array`, especificará se os elementos na matriz podem ser definidos como null. Defina como `true` para indicar que os elementos na matriz podem ser definidos como null; caso contrário, defina como `false`. O valor padrão é `false`. Esse atributo não é usado pelo Visual Studio para fornecer informações do IntelliSense.

  `helpKeyword` Opcional. A palavra-chave para a ajuda F1.

  `locid` Opcional. O identificador para informações de localização sobre o campo. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo de identificador depende do formato especificado na [\<loc>](../ide/loc-javascript.md) marca.

  `value` Opcional. Especifica o código que deve ser avaliado para uso pelo IntelliSense em vez do próprio código de função. Para `<field>` o, esse atributo tem suporte para funções de construtor, mas não tem suporte para literais de objeto. Você pode usar esse atributo para fornecer informações de tipo quando o tipo de campo for indefinido. Por exemplo, você pode usar `value=’1’` para tratar o tipo de campo como um número.

  `description` Opcional. Uma descrição para o campo.

## <a name="remarks"></a>Comentários
 O `name` atributo é necessário quando você está documentando um campo em uma função de construtor. Para todos os outros cenários, todos os atributos para o `<field>` elemento são opcionais.

 Quando você está documentando uma função de construtor, o `<field>` elemento deve aparecer imediatamente antes da declaração de campo. O `name` atributo deve corresponder ao nome do campo que é usado no código-fonte. Para membros de objeto, o `name` atributo poderá ser omitido se o `<field>` elemento aparecer imediatamente antes da declaração de membro de objeto.

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
 O exemplo a seguir mostra como usar o `<field>` elemento com o `static` atributo definido como `true` .

```javascript
function Engine() {
    /// <field name='HorsePower' static='true' type='Number'>static field desc.</field>
}

Engine.HorsePower = 140;
// IntelliSense on the field is available here.
Engine.

```

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar o `<field>` elemento com o `static` atributo definido como `false` .

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

## <a name="see-also"></a>Consulte Também
 [Comentários de documentação XML](../ide/xml-documentation-comments-javascript.md)
