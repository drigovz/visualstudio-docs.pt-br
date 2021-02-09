---
title: Caixa de diálogo Configurar firewall para depuração remota | Microsoft Docs
description: Leia sobre a caixa de diálogo Configurar o firewall para depuração remota, que aparece quando o Firewall do Windows interrompe o recebimento do depurador de dados pela rede.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4fb1d704e2a06ed6c31d6b401b592436c86e4318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99857721"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Caixa de diálogo Configurar Firewall para Depuração Remota
Essa caixa de diálogo aparece quando o Firewall do Windows bloqueia o depurador de receber informações sobre a rede. Para continuar a depuração remota, você deverá abrir um buraco no firewall para que o depurador possa receber informações.

> [!CAUTION]
> Abrir um buraco no firewall pode expor o computador a ameaças de segurança que o firewall é criado para bloquear. Abrir um buraco para depuração remota desbloqueia as portas 4020 e 4021 no Visual Studio 2015. Em outras versões do Visual Studio, outros números de porta são usados. Para obter mais informações, consulte [atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Além disso, isso permite que o depurador abra portas adicionais. Para obter mais informações, consulte [Configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Cancelar depuração remota** Cancela a tentativa de depuração remota. As configurações de segurança de seu computador permanecem intactas.

 **Desbloquear a depuração remota de computadores na rede local (sub-rede)** Habilita a depuração remota de computadores em sua sub-rede local. Isso pode abrir vulnerabilidades em computadores em sua subrede local, mas o firewall continua a bloquear informações que vêm de fora da subrede.

 **Desbloquear a depuração remota de qualquer computador** Habilita a depuração remota de máquinas em qualquer lugar na rede. Essa configuração é a menos segura.

## <a name="see-also"></a>Confira também

- [Segurança do depurador](../debugger/debugger-security.md)
- [Depuração remota](../debugger/remote-debugging.md)
- [Referência de interface do usuário de depuração](../debugger/debugging-user-interface-reference.md)