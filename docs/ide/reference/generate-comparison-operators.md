---
title: Gerar operadores de comparação para o IComparable
ms.custom: SEO-VS-2020
description: Para aumentar o desempenho, gere operadores de comparação para tipos que implementam IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ee0ac916bcc13e6bc89485171b2ce145b31dd919
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932560"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Gerar operadores de comparação para tipos que implementam IComparable

Esta geração de código aplica-se a:

- C#

**O que:** Permite gerar operadores de **comparação** para tipos que implementam IComparable.

**Quando:** Você tem um tipo que implementa IComparable, adicionaremos automaticamente os operadores de comparação.

**Por que:** Se você estiver implementando um tipo de valor, considere substituir o método **Equals** para obter um desempenho maior sobre a implementação padrão do método Equals em ValueType.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor dentro da classe ou na palavra-chave IComparable.

2. Depois, siga um destes procedimentos:

   - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

   - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.

   - Clique no ícone ![chave de fenda](../media/screwdriver-icon.png) ícone que aparece na margem esquerda.

   ![Gerar Operadores de Comparação](media/generate-comparison-operators.png)

3. Selecione **gerar Equals (Object)** no menu suspenso.

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
