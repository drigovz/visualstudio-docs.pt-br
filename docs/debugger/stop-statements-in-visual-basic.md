---
title: Instruções Stop em Visual Basic | Microsoft Docs
description: Examine a instrução Visual Basic stop, que fornece uma alternativa programática para definir um ponto de interrupção no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a17aafd508acd9272e8058ea7ca3ff585a8c0c8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904930"
---
# <a name="stop-statements-in-visual-basic"></a>Instruções Stop no Visual Basic

A instrução Stop do Visual Basic fornece uma alternativa programática ao definir um ponto de interrupção. Quando o depurador encontrar uma instrução Stop, ele interromperá a execução do programa (entra em modo de interrupção). Os programadores C# podem obter o mesmo efeito usando uma chamada para <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Você define ou remove uma instrução Stop editando o código-fonte. Você não pode definir ou limpar instruções Stop usando os comandos do depurador, como se fosse um ponto de interrupção.

Ao contrário de uma instrução End, a instrução Stop não redefine variáveis ou retorna você ao modo de design. Você pode escolher Continuar no menu Depurar para continuar a execução do aplicativo.

Quando você executar um aplicativo Visual Basic fora do depurador, uma instrução Stop iniciará o depurador se a depuração Just-in-time estiver habilitada. Se a depuração Just-in-time não estiver habilitada, a instrução Stop se comparecerá como se fosse uma instrução End e encerrará a execução. Nenhum evento do QueryUnload ou Unload ocorrerá, por isso, você deverá remover todas as instruções Stop da versão de lançamento do aplicativo do Visual Basic. Para obter mais informações, confira [Depuração Just-In-Time](just-in-time-debugging-in-visual-studio.md).

 Para evitar ter que remover as instruções Stop, você pode usar a compilação condicional:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Outra alternativa é usar uma <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> instrução em vez da instrução Stop. Uma <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> instrução quebra a execução somente quando uma condição especificada não é atendida. <xref:System.Diagnostics.Debug.Assert%2A> as instruções são removidas automaticamente quando você cria uma versão de lançamento. Para obter mais informações, confira [Asserções em código gerenciado](assertions-in-managed-code.md). Se você quiser uma <xref:System.Diagnostics.Debug.Assert%2A> instrução que sempre interrompa a execução na versão de depuração, você pode fazer isso:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Outra alternativa é usar o <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> método:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Confira também

- [Segurança do depurador](debugger-security.md)
- [Tipos de projeto C#, F# e Visual Basic](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Depurando código gerenciado](debugging-managed-code.md)
