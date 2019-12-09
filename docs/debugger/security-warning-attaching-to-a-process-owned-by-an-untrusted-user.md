---
title: 'Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou se você não tiver certeza, não anexe a este processo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729770"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Aviso de segurança: anexar a um processo pertencente a um usuário não confiável pode ser perigoso. Se as informações a seguir parecerem suspeitas ou, se você não tiver certeza, não anexe a esse processo
Essa caixa de diálogo de aviso é exibida quando você anexa a um processo que contém o código parcialmente confiável ou seja de propriedade de um usuário não confiável imediatamente antes de ocorrer a anexação. Um processo não confiável que contém o código mal-intencionado tem o potencial de danificar o computador que faz a depuração. Se você tiver razão para desconfiar do processo, clique em **Cancelar** para evitar a depuração.

 Para suprimir esse aviso ao depurar um cenário legítimo, feche o Visual Studio e defina o valor dessa chave do registro como 1: `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning` e reinicie o Visual Studio. Depois de concluir a depurar do cenário, redefina o valor como 0 e reinicie o Visual Studio.

 Os “Usuários confiáveis” incluem você, mais um conjunto de usuários padrão que são definidos normalmente em computadores que têm o .NET Framework instalado, por exemplo, `aspnet`, `localsystem`, `networkservice` e `localservice`.

## <a name="uielement-list"></a>Lista UIElement
 Nome do nome do assembly solicitado para depurar

 Usuário atual usuário

 Anexar Pressione para continuar a depuração anexando

 Não anexar ao processo

## <a name="see-also"></a>Consulte também
- [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Segurança do depurador](../debugger/debugger-security.md)