---
title: Conclusão de DateTime e TimeSpan por meio do menu IntelliSense
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471540"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Conclusão de DateTime e TimeSpan por meio do menu IntelliSense

Esta refatoração aplica-se a:

- C#

**O que:** A cadeia de caracteres DateTime e TimeSpan literal e o preenchimento da cadeia de caracteres de formato pelo menu IntelliSense.

**Quando:** Você deseja gravar uma cadeia de caracteres DateTime e TimeSpan literal e uma cadeia de caracteres de formato. O IntelliSense fornece uma conclusão básica e uma explicação sobre o que significa cada um dos caracteres. 

**Por que:** Lembrar de formatos DateTime é difícil e o IntelliSense pode ajudá-lo a escrevê-lo.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na cadeia de caracteres de formato DateTime ou TimeSpan.
2. Pressione **Ctrl** + **espaço** para disparar o menu **IntelliSense** .
3. Selecione o caractere que você deseja adicionar.

   ![Conclusão de DateTime do IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>Veja também

- [Refatoração](../refactoring-in-visual-studio.md)
