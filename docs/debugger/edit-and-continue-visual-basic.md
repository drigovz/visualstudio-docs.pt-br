---
title: Editar e continuar (Visual Basic) | Microsoft Docs
description: Editar e continuar está disponível para projetos de Visual Basic. Saiba quais edições têm suporte e como pode controlar se, e quando, suas edições são aplicadas.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f5df9910d779a4c360a0c1f3b6482b5c51256d29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871917"
---
# <a name="edit-and-continue-visual-basic"></a>Editar e Continuar (Visual Basic)
Editar e Continuar são um recurso para depuração do [!INCLUDE [vbprvb](../code-quality/includes/vbprvb_md.md)] que permite alterar seu código durante a execução em modo de interrupção. Depois que as edições do código tiverem sido aplicadas, você poderá retomar a execução de código com as novas edições no lugar e visualizar o efeito.

 Você pode usar o recurso Editar e Continuar sempre que entrar no modo de Interrupção. No modo de interrupção, o ponteiro de instrução, uma ponta de seta amarela na janela de origem, aponta para a linha que contém uma instrução executável em um corpo de método ou propriedade que será executado em seguida.

 Editar e Continuar dá suporte à maioria das alterações que você talvez queira fazer durante uma sessão de depuração, mas há algumas exceções. Para obter mais informações, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Quando você faz uma edição não autorizada, a alteração será marcada com um sublinhado ondulado roxo e uma tarefa será exibida na Lista de Tarefas. Você deve desfazer uma edição não autorizada se quiser continuar usando Editar e Continuar. Certas edições não autorizadas podem ser permitidas se forem feitas fora de Editar e Continuar. Se você quiser reter os resultados de uma edição não autorizada, deverá parar de depurar e reiniciar o aplicativo.

 Editar e continuar tem suporte em aplicativos UWP para Windows 10, e aplicativos x86 e x64 direcionados para a área de trabalho .NET Framework 4,6 ou versões posteriores (o .NET Framework é apenas uma versão da área de trabalho).

 > [!NOTE]
 > Aplicativos e plataformas sem suporte incluem ASP.NET 5, Silverlight 5 e Windows 8.1.

 Editar e Continuar não tem suporte quando você começa a depuração usando **Anexar ao Processo**. Editar e continuar não tem suporte para código otimizado ou código nativo e gerenciado Misto. Para obter mais informações, consulte [alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md).

 Os tópicos desta seção fornecem detalhes adicionais sobre como usar esse recurso e que tipos de alterações não são permitidas.

## <a name="in-this-section"></a>Nesta seção
 [Como: aplicar edições no modo de interrupção com editar e continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md) Explica como aplicar edições de código no modo de interrupção.

 [Alterações de código com suporte (C# e Visual Basic)](../debugger/supported-code-changes-csharp.md) Descreve os tipos de edição que não podem ser executados em [!INCLUDE [vb_current_short](../debugger/includes/vb_current_short_md.md)] Editar e continuar.

## <a name="related-sections"></a>Seções relacionadas
 [Editar e continuar](../debugger/edit-and-continue.md) Fornece uma lista de tópicos sobre editar e continuar.
