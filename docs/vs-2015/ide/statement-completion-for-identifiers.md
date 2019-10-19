---
title: Conclusão de instrução para identificadores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643856"
---
# <a name="statement-completion-for-identifiers"></a>Conclusão de instrução para identificadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O JavaScript não permite a digitação explícita de declarações de variáveis. Como resultado, o IntelliSense nem sempre fornece listas de preenchimento para objetos. Isso pode ocorrer em várias situações. Veja a seguir alguns outros comuns.

- Um parâmetro é declarado, mas não foi chamado em outro lugar no documento ativo, conforme mostrado no exemplo a seguir.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- Um objeto está em uma função que é chamada em resposta a um evento. No momento do design, o mecanismo do IntelliSense não pode determinar o tipo dos objetos usados nessa situação.

   Se o mecanismo do IntelliSense puder determinar que o evento deve ser chamado, normalmente com o uso de `addEventListener` para o evento no documento ativo, serão fornecidas informações mais precisas do IntelliSense.

  Quando o IntelliSense não consegue identificar um objeto, o mecanismo do IntelliSense popula a lista de conclusão com entidades nomeadas ou identificadores que estão presentes no documento ativo. Quando a lista de conclusão contém esses identificadores, os ícones de informações aparecem ao lado deles. Além disso, uma dica de ferramenta para cada identificador indica que a expressão é desconhecida. A ilustração a seguir mostra as opções de conclusão de instrução para um objeto do tipo `light` que não pode ser identificado porque o objeto e suas propriedades são indefinidos. No entanto, a propriedade `intensity` está disponível na lista de identificadores porque ela foi usada na função `illuminate`.

  **Opções de conclusão para um objeto que não pode ser identificado**

  ![IntelliSense do JavaScript para identificadores](../ide/media/js-intellisense-identifiers.png "|::ref1::|")

  Você pode substituir a lista de conclusão de um objeto usando comentários de documentação XML ou recursos de extensibilidade do JavaScript IntelliSense. Usando esses recursos, você pode fornecer informações de tipo e informações mais descritivas do IntelliSense quando ele pode não estar disponível de outra forma. Para obter mais informações, consulte [Extending JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) and [CREATE XML Documentation Comments](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).

## <a name="see-also"></a>Veja também
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
