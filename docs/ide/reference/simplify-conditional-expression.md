---
title: Simplificar a expressão condicional
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0242c8c89848e3e76673ddfbca8a27c20605048d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810344"
---
# <a name="simplify-conditional-expression-refactoring"></a>Simplificar a refatoração de expressão condicional

Esta refatoração aplica-se a:

- C#

**O que:** Permite simplificar uma [expressão condicional](/dotnet/csharp/language-reference/operators/conditional-operator).

**Quando:** Você deseja remover o código desnecessário para fornecer mais clareza.

**Por que:** Simplificar uma expressão condicional pode fornecer mais clareza e sintaxe concisa. Essa ferramenta de refatoração executará a tarefa automaticamente em vez de fazer isso manualmente.

## <a name="how-to"></a>Instruções

1. Coloque o cursor na expressão condicional:

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecione **simplificar expressão condicional**

    ![Simplificar a expressão condicional](media/simplify-conditional-expression.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)