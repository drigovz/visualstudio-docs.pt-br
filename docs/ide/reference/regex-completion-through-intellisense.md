---
title: Conclusão de Regex por meio do IntelliSense
ms.date: 06/10/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 75110432f9bba35ce02588032b9a41dece01056b
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033417"
---
# <a name="regex-completion-through-intellisense-menu"></a>Conclusão de Regex por meio do IntelliSense

Esta refatoração aplica-se a:

- C#

**O quê:** Conclusão da expressão regular (regex) por meio do menu do IntelliSense.

**Quando:** Você deseja gravar uma expressão regular com a ajuda do IntelliSense. O IntelliSense fornece conclusão básica e uma explicação sobre o que cada um dos caracteres regex significa. 

**Por que:** Escrever uma expressão regular é difícil e o IntelliSense pode ajudar você a escrevê-la.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na cadeia de caracteres do regex.
2. Pressione **Ctrl**+**espaço** para disparar o menu do **IntelliSense**.
3. Selecione o caractere que você deseja adicionar à sua cadeia de caracteres do regex.

   ![Conclusão do Regex por meio do IntelliSense](../media/regex-completion-intellisense.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
