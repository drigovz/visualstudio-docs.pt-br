---
title: Editar e continuar (Visual Basic) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue, 64-bit
- Edit and Continue [Visual Basic]
- debugging [Visual Basic], Edit and Continue
- Visual Basic, Edit and Continue
- 64-bit Edit and Continue
ms.assetid: 7e90f34f-e699-45ab-a4c9-a4b527c498c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f73b67ac4268c04dfa9ff7ab020891623f528f9b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699243"
---
# <a name="edit-and-continue-visual-basic"></a>Editar e Continuar (Visual Basic)
Editar e Continuar são um recurso para depuração do [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] que permite alterar seu código durante a execução em modo de interrupção. Depois que as edições do código tiverem sido aplicadas, você poderá retomar a execução de código com as novas edições no lugar e visualizar o efeito.

 Você pode usar o recurso Editar e Continuar sempre que entrar no modo de Interrupção. No modo de interrupção, o ponteiro de instrução, uma seta amarela na janela de origem, aponta para a linha que contém uma instrução executável em um corpo de método ou propriedade que será executada em seguida.

 Editar e Continuar dá suporte à maioria das alterações que você talvez queira fazer durante uma sessão de depuração, mas há algumas exceções. Para obter mais informações, consulte [Supported Code Changes (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Quando você faz uma edição não autorizada, a alteração será marcada com um sublinhado ondulado roxo e uma tarefa será exibida na Lista de Tarefas. Você deve desfazer uma edição não autorizada se quiser continuar usando Editar e Continuar. Certas edições não autorizadas podem ser permitidas se forem feitas fora de Editar e Continuar. Se você quiser reter os resultados de uma edição não autorizada, deverá parar de depurar e reiniciar o aplicativo.

 Editar e continuar tem suporte em aplicativos UWP para Windows 10 e o x86 e x64 aplicativos destinados ao .NET Framework 4.6 da área de trabalho ou versões posteriores (.NET Framework é apenas uma versão de área de trabalho).

 > [!NOTE]
 > Plataformas e aplicativos sem suporte incluem o ASP.NET 5, o Silverlight 5 e o Windows 8.1.

 Editar e Continuar não tem suporte quando você começa a depuração usando **Anexar ao Processo**. Editar e continuar não há suporte para código otimizado ou misto código gerenciado e nativo. Para obter mais informações, consulte [Supported Code Changes (c# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Os tópicos desta seção fornecem detalhes adicionais sobre como usar esse recurso e que tipos de alterações não são permitidas.

## <a name="in-this-section"></a>Nesta seção
 [Como: aplicar edições no modo de interrupção com editar e continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) explica como aplicar edições de código no modo de interrupção.

 [Suporte para alterações de código (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md) descreve quais tipos de edições não podem ser executadas no [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] editar e continuar.

## <a name="related-sections"></a>Seções relacionadas
 [Editar e continuar](../debugger/edit-and-continue.md) fornece uma lista de tópicos sobre como editar e continuar.
