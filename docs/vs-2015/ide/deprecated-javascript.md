---
title: '&lt;deprecated&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b93a2b4dcc541f32c16766da0dd9dd19a4fdfe0d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759750"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;deprecated&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Especifica um método ou função preterida.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `type`  
 Opcional. Especifica se a função ou método será removido em uma versão futura, ou se a função ou método já foi removido e que seu uso pode resultar em um erro. Definido como `deprecate` para especificar que a função ou método será removido em uma versão futura. Definido como `remove` para especificar que a função ou método já foi removido.  
  
 `locid`  
 Opcional. O identificador de informações de localização sobre o método ou função. O identificador é um membro ID ou ele corresponde ao `name` valor em um pacote de mensagem definido pelos metadados OpenAjax do atributo. O tipo de identificador depende do formato especificado na [ \<loc >](../ide/loc-javascript.md) elemento.  
  
 `description`  
 Opcional. Uma descrição da função ou método que está sendo preterido.  
  
## <a name="remarks"></a>Comentários  
 Os elementos usados para anotar as funções, que incluem `<deprecated>`, devem ser colocados no corpo da função antes que as instruções. Quando você marca uma função como preteridos, recomendamos que você substitua sua [ \<resumo >](../ide/summary-javascript.md) elemento com o `<deprecated>` elemento.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar o `<deprecated>` elemento.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
