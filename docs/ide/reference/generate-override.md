---
title: Gerar uma substituição de método
description: Saiba como gerar imediatamente o código para qualquer método que possa ser substituído de uma classe base.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5f27adacc39c53bf46b3a2ee09c71ae27b47f928
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617481"
---
# <a name="generate-an-override-in-visual-studio"></a>Gerar uma substituição no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente o código para qualquer método que possa ser substituído de uma classe base.

**Quando:** você quer substituir um método de classe base e gerar a assinatura automaticamente.

**Por quê:** você mesmo poderia escrever a assinatura do método, no entanto, esse recurso gerará automaticamente a assinatura.

## <a name="how-to"></a>Como fazer

1. Digite `override` em C# ou `Overrides` em Visual Basic, seguido por um espaço, em que você deseja inserir um método de substituição.

   - C#:

      ![Substituição do IntelliSense em C#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![Substituição do IntelliSense em VB](media/override-intellisense-vb.png)

2. Selecione o método que você deseja substituir da classe base.

   > [!TIP]
   > - Use o ícone de propriedade ![Ícone de propriedade](media/override-property-cs.png) para mostrar ou ocultar propriedades na lista.
   > - Use o ícone de método ![Ícone de método](media/override-method-cs.png) para mostrar ou ocultar métodos na lista.

   A propriedade ou o método selecionado será adicionado à classe como uma substituição, pronta para ser implementada.

   - C#:

       ![Resultado da substituição em C#](media/override-result-cs.png)

   - Visual Basic:

       ![Resultado da substituição em VB](media/override-result-vb.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
