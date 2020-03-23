---
title: Gerar a refatoração de parâmetro
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 372a3f705e5e85c0edb31a754105f61056402b9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094357"
---
# <a name="generate-parameter"></a>Gerar o parâmetro

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** Gera automaticamente um parâmetro de método.

**Quando:** Você faz referência a uma variável em um método que não existe no contexto atual e recebe um erro; você pode gerar um parâmetro como uma correção de código. 

**Por que:** Você pode modificar rapidamente uma assinatura de método sem perder o contexto.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome da variável e **pressione Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
1. Selecione **Gerar o parâmetro**.

   ![Gerar o parâmetro](media/generate-parameter.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
