---
title: Método embutido
description: Saiba como usar o menu ações rápidas e refatoração no Visual Studio para refatorar declarações de método embutidas e fornecer uma sintaxe mais clara.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 80313cf0dd9b828c9602fdf8ebff022342faa0fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852356"
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
