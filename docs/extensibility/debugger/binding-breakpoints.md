---
title: Pontos de interrupção de vinculação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, binding
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 680cff398a43d1ebe9ccf061ad42781500c7cf01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739238"
---
# <a name="bind-breakpoints"></a>Pontos de interrupção de vinculação
Se o usuário definir um ponto de ruptura, talvez pressionando **F9,** o IDE formula a solicitação e solicita a sessão de depuração para criar o ponto de breakpoint.

## <a name="set-a-breakpoint"></a>Definir um ponto de interrupção
 Definir um ponto de ruptura é um processo de duas etapas, porque o código ou dados afetados pelo breakpoint pode ainda não estar disponível. Primeiro, o ponto de ruptura deve ser descrito e, em seguida, à medida que o código ou os dados se tornam disponíveis, ele deve estar vinculado a esse código ou dados, como segue:

1. O ponto de partida é solicitado a partir dos mecanismos de depuração relevantes (DEs) e, em seguida, o ponto de ruptura é vinculado ao código ou dados à medida que ele se torna disponível.

2. A solicitação de ponto de ruptura é enviada para a sessão de depuração, que a envia para todos os DEs relevantes. Qualquer DE que optar por lidar com o ponto de ruptura cria um ponto de ruptura pendente correspondente.

3. A sessão de depuração coleta os pontos de interrupção pendentes e os envia de volta para o pacote de depuração (o componente de depuração do Visual Studio).

4. O pacote de depuração solicita à sessão de depuração para vincular o ponto de ruptura pendente a código ou dados. A sessão de depuração envia essa solicitação para todos os DEs relevantes.

5. Se o DE for capaz de vincular o ponto de ruptura, ele envia um evento vinculado ao breakpoint de volta à sessão de depuração. Se não, ele envia um evento de erro de ponto de ruptura em vez disso.

## <a name="pending-breakpoints"></a>Pontos de interrupção pendentes
 Um ponto de ruptura pendente pode se ligar a vários locais de código. Por exemplo, uma linha de código-fonte para um modelo C++ pode se ligar a cada seqüência de código gerada a partir do modelo. A sessão de depuração pode usar um evento vinculado a ponto de ruptura para enumerar os contextos de código vinculados a um ponto de ruptura no momento em que o evento foi enviado. Mais contextos de código podem ser vinculados mais tarde, de modo que o DE pode enviar vários eventos vinculados a breakpoint para cada solicitação de vinculação. No entanto, um DE deve enviar apenas um evento de erro de ponto de ruptura por solicitação de vinculação.

## <a name="implementation"></a>Implementação
 Programáticamente, o pacote de depuração chama o gerenciador de depuração de sessão (SDM) e fornece-lhe uma interface [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que envolve uma estrutura [de BP_REQUEST_INFO,](../../extensibility/debugger/reference/bp-request-info.md) que descreve o ponto de ruptura a ser definido. Embora os pontos de interrupção possam ser de muitas formas, eles finalmente se resolvem para um código ou contexto de dados.

 O SDM passa esta chamada para cada DE relevante chamando seu método [CreatePendingBreakpoint.](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) Se o DE optar por lidar com o ponto de ruptura, ele criará e retorna uma interface [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) O SDM coleta essas interfaces e as repassa de `IDebugPendingBreakpoint2` volta para o pacote de depuração como uma única interface.

 Até agora, nenhum evento foi gerado.

 O pacote de depuração tenta vincular o ponto de ruptura pendente ao código ou aos dados, [chamando-o de Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md), que é implementado pelo DE.

 Se o ponto de ruptura estiver vinculado, o DE envia uma interface de evento [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) para o pacote de depuração. O pacote de depuração usa essa interface para enumerar todos os contextos de código (ou o contexto de dados únicos) vinculados ao ponto de interrupção, chamando [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md), que retorna uma ou mais interfaces [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) A interface [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) retorna uma interface [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) e [o GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) retorna uma [união de BP_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-resolution-info.md) que contém o código ou o contexto de dados.

 Se o DE não conseguir vincular o ponto de ruptura, ele envia uma única interface de evento [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) para o pacote de depuração. O pacote de depuração recupera o tipo de erro (erro ou aviso) e a mensagem informacional chamando [GetErrorBreakpoint,](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)seguido por [GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) e [GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md). Isso retorna uma estrutura [BP_ERROR_RESOLUTION_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md) que contém o tipo de erro e a mensagem.

 Se um DE lida com um ponto de ruptura, `BPET_TYPE_ERROR`mas não pode vinculá-lo, ele retorna um erro de tipo . O pacote de depuração responde exibindo uma caixa de diálogo de erro, e o IDE coloca um glifo de exclamação dentro do glifo de ponto de ruptura à esquerda da linha de código fonte.

 Se um DE lida com um ponto de ruptura, não pode vinculá-lo, mas algum outro DE pode ligá-lo, ele retorna um aviso. O IDE responde colocando um glifo de perguntas dentro do glifo de ponto de ruptura à esquerda da linha de código fonte.

## <a name="see-also"></a>Confira também
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
