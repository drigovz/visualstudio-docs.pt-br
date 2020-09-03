---
title: Criar comentários do JSDoc para o JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619268"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Criar comentários JSDoc para JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O IntelliSense no Visual Studio exibe informações que você adiciona a um script usando comentários JSDoc padrão. Você pode usar comentários do JSDoc para fornecer informações sobre elementos de código, como funções, campos e variáveis.

## <a name="jsdoc-comment-tags"></a>Marcas de comentário JSDoc
 As seguintes marcas de comentário JSDoc padrão são usadas pelo IntelliSense para exibir informações sobre seu código.

|  Marca de JSDoc   |                       Syntax                        |                                                     Observações                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated*Descrição* do              |                                   Especifica uma função ou um método preterido.                                   |
| @description |             @description*Descrição* do              |                              Especifica a descrição de uma função ou um método.                               |
|    @param    | @param {*type*} *parameterName*<em>description</em> | Especifica informações para um parâmetro em uma função ou método.<br /><br /> O TypeScript também dá suporte a @paramTag . |
|  @property   |          @property {*type*} *propertyName*          |   Especifica informações, incluindo uma descrição, para um campo ou membro definido em um objeto.    |
|   @returns   |                  @returns {*Type*}                  |           Especifica um valor de retorno.<br /><br /> Para TypeScript, use @returnType em vez de @returns .           |
|   @summary   |               @summary*Descrição* do                |                   Especifica a descrição de uma função ou método (igual a @description ).                   |
|    @type     |                   @type {*Type*}                    |                                Especifica o tipo para uma constante ou uma variável.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            Especifica um tipo personalizado.                                            |

### <a name="examples"></a>Exemplos
 O exemplo a seguir mostra o uso das @description @param marcas, e @return JSDoc para uma função chamada `getArea` .

```javascript
/** @description Determines the area of a circle that has the specified radius parameter.
 * @param {number} radius The radius of the circle.
 * @return {number}
 */
function getArea(radius) {
    var areaVal;
    areaVal = Math.PI * radius * radius;
    return areaVal;
}
```

 No exemplo anterior, o IntelliSense mostra a descrição, o parâmetro e as informações de retorno quando você digita o parêntese de abertura para `getArea` .

 ![Informações do IntelliSense para uma função](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 O exemplo a seguir mostra como usar a @typedef marca com a @property marca.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 O exemplo a seguir mostra o uso das @type marcas JSDoc. Como mostrado neste exemplo, os asteriscos únicos (*) que seguem o par de asterisco inicial ( \* \* ) não são necessários.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 O exemplo a seguir mostra como usar a @deprecated marca JSDoc.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
