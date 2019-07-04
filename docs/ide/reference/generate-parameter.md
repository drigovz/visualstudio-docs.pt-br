---
title: Gerar a refatoração de parâmetro
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329057"
---
# <a name="generate-parameter"></a>Gerar o parâmetro

Esta refatoração aplica-se a:

- C#

**O quê:** gera automaticamente um parâmetro de método.

**Quando:** fazer referência a uma variável em um método que não existe no contexto atual e receber um erro; você pode gerar um parâmetro como uma correção de código. 

**Por que:** você pode modificar rapidamente uma assinatura de método sem perder o contexto.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome da variável e pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.
1. Selecione **Gerar o parâmetro**.

   ![Gerar o parâmetro](media/generate-parameter.png) 

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
