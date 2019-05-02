---
title: Criar comentários JSDoc para JavaScript IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4d300651731b38b9b86421d36d9de169dc6464d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651039"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Criar comentários JSDoc para JavaScript IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O IntelliSense no Visual Studio exibe informações que você adiciona um script usando os comentários em JSDoc padrão. Você pode usar os comentários JSDoc para fornecer informações sobre os elementos de código como funções, campos e variáveis.  

## <a name="jsdoc-comment-tags"></a>Marcas de comentário JSDoc  
 As seguintes marcas de comentário JSDoc padrão são usadas pelo IntelliSense para exibir informações sobre seu código.  

|  Marcação de JSDoc   |                       Sintaxe                        |                                                     Observações                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *description*              |                                   Especifica um método ou função preterida.                                   |
| @description |             @description *description*              |                              Especifica a descrição de uma função ou método.                               |
|    @param    | @param {*type*} *parameterName*<em>description</em> | Especifica informações de um parâmetro em uma função ou método.<br /><br /> TypeScript também dá suporte a @paramTag. |
|  @property   |          @property {*type*} *propertyName*          |   Especifica as informações, incluindo uma descrição, para um campo ou um membro que é definido em um objeto.    |
|   @returns   |                  @returns {*type*}                  |           Especifica um valor de retorno.<br /><br /> Para o TypeScript, use @returnType em vez de @returns.           |
|   @summary   |               @summary *description*                |                   Especifica a descrição de uma função ou método (mesmo que @description).                   |
|    @type     |                   @type {*type*}                    |                                Especifica o tipo para uma constante ou uma variável.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            Especifica um tipo personalizado.                                            |

### <a name="examples"></a>Exemplos  
 O exemplo a seguir mostra o uso do @description, @param, e @return JSDoc marcas para uma função chamada `getArea`.  

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

 No exemplo anterior, o IntelliSense mostra a descrição, parâmetros e retornam informações quando você digita o parêntese de abertura para `getArea`.  

 ![Informações de IntelliSense para uma função](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 O exemplo a seguir mostra como usar o @typedef marcar com o @property marca.  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 O exemplo a seguir mostra o uso do @type JSDoc marcas. Conforme mostrado neste exemplo, único asteriscos (*) que seguem o par de asterisco inicial (\*\*) não são necessários.  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 O exemplo a seguir mostra como usar o @deprecated a marcação de JSDoc.  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```
