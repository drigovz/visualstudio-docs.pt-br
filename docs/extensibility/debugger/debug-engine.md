---
title: Motor de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines
ms.assetid: 148b1efc-ca07-4d8e-bdfc-c723a760c620
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a4cb00796f8db23a43cd81a06d80d0fac40f075e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739059"
---
# <a name="debug-engine"></a>Motor de depuração
Um mecanismo de depuração (DE) trabalha com o intérprete ou sistema operacional para fornecer serviços de depuração, como controle de execução, pontos de interrupção e avaliação de expressão. O DE é responsável por monitorar o estado de um programa que está sendo depurado. Para isso, o DE usa todos os métodos disponíveis para ele no tempo de execução suportado, seja a partir da CPU ou de APIs fornecidas pelo tempo de execução.

 Por exemplo, o CLR (Common Language runtime, tempo de execução) fornece mecanismos para monitorar um programa em execução através das interfaces ICorDebugXXX. Um DE que suporta o CLR usa as interfaces ICorDebugXXX apropriadas para acompanhar um programa de código gerenciado sendo depurado. Em seguida, ele comunica quaisquer alterações de estado para o Gerenciador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração de sessão (SDM), que encaminha essas informações para o IDE.

> [!NOTE]
> Um mecanismo de depuração tem como alvo um tempo de execução específico, ou seja, o sistema no qual o programa que está sendo depurado é executado. O CLR é o tempo de execução para código gerenciado, e o tempo de execução do Win32 é para aplicativos nativos do Windows. Se o idioma criado pode atingir um [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desses dois tempos de execução, já fornece os motores de depuração necessários. Tudo que você tem que implementar é um avaliador de expressão.

## <a name="debug-engine-operation"></a>Operação do motor de depuração
 Os serviços de monitoramento são implementados através das interfaces DE e podem fazer com que o pacote de depuração seja transicionado entre diferentes modos operacionais. Para obter mais informações, consulte [Modos operacionais](../../extensibility/debugger/operational-modes.md). Normalmente, há apenas uma implementação DE por ambiente de tempo de execução.

> [!NOTE]
> Embora existam implementações DE separadas para [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)]Transact-SQL e, VBScript e [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] compartilhe um único DE.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]A depuração permite que os mecanismos de depuração [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] executem uma das duas maneiras: no mesmo processo que o shell, ou no mesmo processo que o programa de destino que está sendo depurado. Esta última forma geralmente ocorre quando o processo que está sendo depurado é na verdade um script em execução sob um intérprete. O motor de depuração deve ter conhecimento íntimo do intérprete para monitorar o roteiro. Neste caso, o intérprete é, na verdade, um tempo de execução; os motores de depuração são para implementações específicas de tempo de execução. Além disso, a implementação de um único DE pode ser dividida entre os limites de processo e máquina (por exemplo, depuração remota).

 O DE expõe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] as interfaces de depuração. Toda comunicação é através do COM. Se o DE está carregado no processo, fora de processo ou em outro computador, ele não afeta a comunicação de componentes.

 O DE trabalha com um componente avaliador de expressão para permitir que o DE para esse tempo de execução em particular para entender a sintaxe das expressões. O DE também funciona com um componente manipulador de símbolos para acessar as informações simbólicas de depuração geradas pelo compilador de idiomas. Para obter mais informações, consulte [o avaliador de expressão](../../extensibility/debugger/expression-evaluator.md) e o provedor de [símbolos](../../extensibility/debugger/symbol-provider.md).

## <a name="see-also"></a>Confira também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
- [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md)
- [Provedor de símbolos](../../extensibility/debugger/symbol-provider.md)
