---
title: Método embutido
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402229"
---
# <a name="inline-method"></a>Método embutido

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Refatoração de método embutido. 

**Quando:** Você deseja substituir os usos de um método estático, de instância e de extensão em um único corpo de instrução com uma opção para remover a declaração de método original.

**Por que:**  Essa refatoração fornecerá uma sintaxe mais clara.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor sobre o uso do método.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecione uma das seguintes opções: 
    
   Selecione **Embutir `<QualifiedMethodName>`** para remover a declaração de método embutido: 

    ![Tornar a classe abstrata](media/inline-method-remove-declaration.png)

   Selecione **Embutir e manter `<QualifiedMethodName>`** para preservar a declaração de método original: 

    ![Tornar a classe abstrata](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
