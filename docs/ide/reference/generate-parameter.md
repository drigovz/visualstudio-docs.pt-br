---
title: Gerar a refatoração de parâmetro
description: Saiba como usar o menu ações rápidas e refatoração para gerar automaticamente um parâmetro de método.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 33e2be19e3a5a83d89e722aa0c1a1154c8196939
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968028"
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

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
