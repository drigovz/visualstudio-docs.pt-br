---
title: Modos Operacionais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738283"
---
# <a name="operational-modes"></a>Modos operacionais
Existem três modos em que o IDE pode operar, da seguinte forma:

- [Modo de design](#vsconoperationalmodesanchor1)

- [Modo de execução](#vsconoperationalmodesanchor2)

- [Modo de interrupção](#vsconoperationalmodesanchor3)

  Como o motor de depuração personalizado (DE) transita entre esses modos é uma decisão de implementação que exige que você esteja familiarizado com os mecanismos de transição. O DE pode ou não implementar diretamente esses modos. Esses modos são realmente depurar modos de pacote que alternam com base na ação do usuário ou eventos do DE. Por exemplo, a transição do modo de execução para o modo de quebra é instigada por um evento de parada do DE. A transição da pausa para o modo de execução ou do modo de passo é instigada pelo usuário que realiza operações como Step ou Execute. Para obter mais informações sobre as transições de DE, consulte [Controle de execução](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Modo de design
 O modo de design é o estado não executado da depuração do Visual Studio, durante o qual você pode definir recursos de depuração em seu aplicativo.

 Apenas alguns recursos de depuração são usados durante o modo de design. Um desenvolvedor pode optar por definir pontos de interrupção ou criar expressões de relógio. O DE nunca é carregado ou chamado enquanto o IDE está no modo de design. A interação com o DE ocorre apenas durante os modos de execução e quebra.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Modo de execução
 O modo de execução ocorre quando um programa é executado em uma sessão de depuração no IDE. O aplicativo é executado até o término, até que um ponto de interrupção seja atingido, ou até que uma exceção seja lançada. Quando o aplicativo é executado até o término, o DE passa para o modo de design. Quando um ponto de ruptura é atingido ou uma exceção é lançada, o DE faz a transição para o modo de quebra.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Modo de quebra
 O modo de quebra ocorre quando a execução do programa de depuração é suspensa. O modo break oferece ao desenvolvedor um instantâneo do aplicativo no momento da pausa e permite que o desenvolvedor analise o estado do aplicativo e altere como o aplicativo será executado. O desenvolvedor pode visualizar e editar código, examinar ou modificar dados, reiniciar o aplicativo, finalizar a execução ou continuar a execução a partir do mesmo ponto.

 O modo de quebra é inserido quando o DE envia um evento de parada síncrona. Eventos de parada síncronos, também chamados de eventos de interrupção, notificam o Gerenciador de depuração de sessão (SDM) e o IDE de que o aplicativo que está sendo depurado parou de executar o código. As interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) são exemplos de eventos de interrupção.

 Os eventos de interrupção são continuados por uma chamada para um dos seguintes métodos, que transitam o depurador do modo de pausa para o modo de execução ou passo:

- [Executar](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Etapa](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuar](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Modo passo
 O modo passo ocorre quando o programa se aproxima da próxima linha de código, ou para, sobre ou fora de uma função. Um passo é executado chamando o método [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Este método `DWORD`requer s que especifiquem as enumerações [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) como parâmetros de entrada.

 Quando o programa é degraus para a próxima linha de código ou para uma função, ou ele é executado para o cursor ou para um ponto de ruptura definido, o DE automaticamente volta para o modo de quebra.

## <a name="see-also"></a>Confira também
- [Controle da execução](../../extensibility/debugger/control-of-execution.md)
