---
title: Depuração F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92f570aece9d68e2a4be20c3487137e085e33001
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851894"
---
# <a name="debugging-f"></a>Depurando F\#
A depuração de F# é semelhante à depuração de qualquer linguagem gerenciada, com algumas exceções:

- A janela **Autos** não exibe as variáveis de F#.

- Não há suporte para Editar e Continuar em F#. As edições ao código F# durante uma sessão de depuração são possíveis, mas devem ser evitadas. Como as alterações de código não são aplicadas durante a sessão de depuração, a edição do código F# durante a depuração causará uma incompatibilidade entre o código-fonte e o código que está sendo depurado.

- O depurador não reconhece expressões de F#. Para inserir uma expressão em uma janela ou uma caixa de diálogo do depurador durante a depuração de F#, você deve traduzir a expressão para a sintaxe do C#. Quando você traduzir uma expressão F# em C#, lembre-se de que o C# usa == como o operador de comparação para igualdade, enquanto o F# usa o = simples.

## <a name="see-also"></a>Consulte também
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
