---
title: Gerar a refatoração de parâmetro
description: Saiba como usar o menu ações rápidas e refatoração para gerar automaticamente um parâmetro de método.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 21e209f5be9072390df58e78db34811f886fa9c5
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617143"
---
# <a name="generate-parameter"></a>Gerar o parâmetro

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Gera automaticamente um parâmetro de método.

**Quando:** Você faz referência a uma variável em um método que não existe no contexto atual e recebe um erro; Você pode gerar um parâmetro como uma correção de código. 

**Por que:** Você pode modificar rapidamente uma assinatura de método sem perder o contexto.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor no nome da variável e pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
1. Selecione **Gerar o parâmetro**.

   ![Gerar o parâmetro](media/generate-parameter.png) 

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
