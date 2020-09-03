---
title: Criar comentários de documentação XML para IntelliSense JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21fdc15b161b7d1cef30effe82e518a174bc9666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619543"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Criar comentários da documentação XML para o JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os *comentários de documentação XML* são comentários JavaScript que você adiciona a um script para fornecer informações sobre elementos de código, como funções, campos e variáveis. No Visual Studio, essas descrições de texto são exibidas com o IntelliSense quando você faz referência à função de script.

 Este tópico fornece um tutorial básico sobre como usar comentários de documentação XML. Para obter informações sobre como usar outros elementos, como [\<var>](../ide/var-javascript.md) e e [\<value>](../ide/value-javascript.md) para exemplos de código adicionais, consulte [comentários de documentação XML](../ide/xml-documentation-comments-javascript.md). Para obter informações sobre como fornecer informações do IntelliSense para um retorno de chamada assíncrono, como um `Promise` , consulte [\<returns>](../ide/returns-javascript.md) .

> [!NOTE]
> Os comentários da documentação XML estão disponíveis somente em assemblies, serviços e arquivos referenciados.

### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Para criar comentários de documentação XML para uma função JavaScript

- Na função, adicione [\<summary>](../ide/summary-javascript.md) , [\<param>](../ide/param-javascript.md) e os [\<returns>](../ide/returns-javascript.md) elementos e preceda cada elemento com três barras de marcas (///).

    > [!NOTE]
    > Cada elemento deve estar em uma única linha.

     O exemplo a seguir mostra uma função JavaScript.

    ```javascript
    function getArea(radius)
    {
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>
        /// <param name="radius" type="Number">The radius of the circle.</param>
        /// <returns type="Number">The area.</returns>
        var areaVal;
        areaVal = Math.PI * radius * radius;
        return areaVal;
    }
    ```

- Para exibir os comentários de documentação XML, digite o nome e o parêntese de abertura de uma função que está marcada com comentários de documentação XML, como no exemplo a seguir:

    ```javascript
    var areaVal = getArea(
    ```

     Quando você digita o parêntese de abertura da função que contém os comentários de documentação XML, o editor de código usa o IntelliSense para exibir as informações definidas nos comentários de documentação XML.

### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Para criar comentários de documentação XML para um campo JavaScript

- Em uma função de construtor ou definição de objeto, adicione um [\<field>](../ide/field-javascript.md) elemento precedido por três barras (///).

     O exemplo a seguir mostra o uso do `<field>` elemento em uma função de construtor. Para obter exemplos adicionais, consulte [\<field>](../ide/field-javascript.md) .

    ```javascript
    function Engine() {
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>
        this.HorsePower = 150;
    }
    ```

- Para exibir os comentários de documentação XML, crie um objeto usando o construtor de função que é marcado com comentários de documentação XML, como no exemplo a seguir.

    ```javascript
    var eng = new Engine();
    ```

- Na próxima linha, digite o nome do objeto e um ponto para mostrar as informações do IntelliSense para o campo.

    ```javascript
    eng.
    ```

### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Para criar comentários de documentação XML para uma função sobrecarregada

1. Na função, adicione um [\<signature>](../ide/signature-javascript.md) elemento para cada sobrecarga. Nesses elementos, adicione outros elementos, como `<summary>` , `<param>` e `<returns>` , antes de cada elemento com três barras de marcas (///).

     O exemplo a seguir mostra uma função JavaScript sobrecarregada. Neste exemplo, as sobrecargas diferem por tipo de parâmetro.

    ```javascript
    function calc(a) {
        /// <signature>
        /// <summary>Function summary 1.</summary>
        /// <param name="a" type="Number">A number.</param>
        /// <returns type="Number" />
        /// </signature>
        /// <signature>
        /// <summary>Function summary 2.</summary>
        /// <param name="a" type="String">A string.</param>
        /// <returns type="Number" />
        /// </signature>
        return a;
    }
    ```

2. Para exibir os comentários de documentação XML, digite o nome e o parêntese de abertura da função que está marcada com comentários de documentação XML, como no exemplo a seguir:

    ```javascript
    calc(
    ```

### <a name="to-create-localized-intellisense"></a>Para criar o IntelliSense localizado

1. Crie um arquivo XML que tenha comentários de documentação no formato OpenAjax MessageBundle.

    > [!IMPORTANT]
    > MessageBundle é o formato recomendado. Não há suporte para esse formato no Microsoft Ajax ou em arquivos. winmd. Para obter informações sobre como usar o `VSDoc` formato alternativo, consulte [\<loc>](../ide/loc-javascript.md) .

     O exemplo a seguir mostra o conteúdo em um arquivo sidecar que contém as informações localizadas do IntelliSense. Esse é um arquivo XML que está localizado em uma pasta específica de cultura, como JA. A pasta deve estar no mesmo local que o arquivo. js que contém o `<loc>` elemento. O nome de arquivo do arquivo XML deve corresponder ao `filename` parâmetro especificado no `<loc>` elemento.

    ```
    <messagebundle>
      <msg name="1">A class that represents a rectangle</msg>
      <msg name="2">The length of the rectangle</msg>
      <msg name="3">The height of the rectangle</msg>
    </messagebundle>

    ```

2. No seu arquivo. js, adicione o código a seguir. O `<loc>` elemento deve ser declarado antes de qualquer script e segue as mesmas regras de uso que `<reference>` o elemento. Para obter mais informações, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md) e [\<loc>](../ide/loc-javascript.md) .

    ```javascript
    /// <loc filename="messageFilename.xml" format="messagebundle"/>

    ```

3. No seu arquivo. js, adicione os elementos de documentação XML e as descrições padrão. Defina os `locid` valores de atributo para corresponder aos `name` valores de atributo correspondentes do arquivo sidecar. As descrições padrão serão substituídas pelas informações localizadas do IntelliSense, se estiverem disponíveis.

    ```javascript
    function add(a,b)
    {
        /// <summary locid='1'>description</summary>
        /// <param name='a' locid='2'>parameter a description</param>
        /// <param name='b' locid='3'>parameter b description</param>
    }

    ```

4. Para exibir os comentários de documentação XML, digite o nome e o parêntese de abertura da função, como no exemplo a seguir:

    ```javascript
    add(
    ```

## <a name="see-also"></a>Consulte Também
 [Comentários de documentação XML](../ide/xml-documentation-comments-javascript.md) do [JavaScript IntelliSense](../ide/javascript-intellisense.md) [NIB: Walkthrough: JavaScript IntelliSense in ASP.net](https://msdn.microsoft.com/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)
