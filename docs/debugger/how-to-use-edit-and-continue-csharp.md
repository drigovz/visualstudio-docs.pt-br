---
title: Usar editar e continuar (C#) | Microsoft Docs
description: Use editar e continuar para fazer e aplicar alterações ao seu código no modo de interrupção durante a depuração, sem interromper e reiniciar a sessão de depuração no Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a0f8126689c0874c984a679da9b6debcb66a3075
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150646"
---
# <a name="how-to-use-edit-and-continue-c"></a>Como usar Editar e Continuar (C#)
Com editar e continuar, você pode fazer e aplicar alterações ao seu código no modo de interrupção durante a depuração, sem precisar parar e reiniciar a sessão de depuração.

Editar e continuar para C# ocorre automaticamente quando você faz alterações de código no modo de interrupção, depois continua a depuração usando **continue**, **Step** ou **Set Next Statement** ou avalia uma função em uma janela do depurador.

Para obter mais informações, consulte [Editar e continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md).

>[!NOTE]
>Não há suporte para editar e continuar para o código de integração de Common Language Runtime (CLR) otimizado, misto ou SQL Server. Para obter informações sobre outros cenários sem suporte, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md). Se você tentar editar e continuar com um desses cenários, será exibida uma caixa de mensagem informando que não há suporte para editar e continuar.

**Para habilitar ou desabilitar editar e continuar:**

1. Se você estiver em uma sessão de depuração, pare a depuração (**depurar**  >  **parar depuração** ou **Shift** + **F5**).

1. Em **ferramentas**  >  **Opções** (ou   >  **Opções** de depuração) > **depuração**  >  **geral**, marque ou desmarque a caixa de seleção **habilitar editar e continuar** .

A configuração entra em vigor quando você inicia ou reinicia a sessão de depuração.

**Para usar editar e continuar:**

1. Durante a depuração, no modo de interrupção, faça uma alteração no código-fonte.

1. No menu **Depurar**, clique em **Continuar**, **Etapa** ou **Definir Próxima Instrução** ou avalie uma função em uma janela de depuração.

   A depuração continua com o novo código compilado.

Não há suporte para alguns tipos de alterações de código por editar e continuar. Para obter mais informações, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).
