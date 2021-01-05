---
title: Método embutido
description: Saiba como usar o menu ações rápidas e refatoração no Visual Studio para refatorar declarações de método embutidas e fornecer uma sintaxe mais clara.
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
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761414"
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

    ![Screeenshot do menu ações rápidas e refatoração no Visual Studio com a conversão das alterações de código ' embutido ' createwidget () ' selecionadas e C# mostradas.](media/inline-method-remove-declaration.png)

   Selecione **Embutir e manter `<QualifiedMethodName>`** para preservar a declaração de método original: 

    ![Screeenshot do menu ações rápidas e refatoração no Visual Studio com a conversão de ' embutido e manter ' createwidget () ' selecionado e alterações de código em C# mostradas.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
