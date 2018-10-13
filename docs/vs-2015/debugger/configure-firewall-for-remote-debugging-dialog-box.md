---
title: Configurar o Firewall para a caixa de diálogo de depuração remota | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d273d1158d2a0d3c867605bc4f43a40be8e38314
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188546"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Caixa de diálogo Configurar Firewall para Depuração Remota
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa caixa de diálogo aparece quando o Firewall do Windows bloqueia o depurador de receber informações sobre a rede. Para continuar a depuração remota, você deverá abrir um buraco no firewall para que o depurador possa receber informações.  
  
> [!CAUTION]
>  Abrir um buraco no firewall pode expor o computador a ameaças de segurança que o firewall é criado para bloquear. Abrir um buraco para depuração remota desbloqueia as portas 4020 e 4021 no Visual Studio 2015. Em outras versões do Visual Studio, outros números de porta são usados. Para obter mais informações, consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md). Além disso, isso permite que o depurador abra portas adicionais. Para obter mais informações, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Lista UIElement  
 **Cancelar a depuração remota**  
 Cancela a tentativa de depuração remota. As configurações de segurança de seu computador permanecem intactas.  
  
 **Desbloquear a depuração remota de computadores na rede local (sub-rede)**  
 Habilita a depuração remota de computadores em sua subrede local. Isso pode abrir vulnerabilidades em computadores em sua subrede local, mas o firewall continua a bloquear informações que vêm de fora da subrede.  
  
 **Desbloquear a depuração remota de qualquer computador**  
 Habilita a depuração remota de computadores em qualquer lugar na rede. Essa configuração é a menos segura.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Configurar as ferramentas remotas no dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Referência da interface do usuário de depuração](../debugger/debugging-user-interface-reference.md)



