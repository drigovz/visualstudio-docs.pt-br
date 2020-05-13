---
title: Controle de Programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738233"
---
# <a name="program-control"></a>Controle do programa
Na depuração do Visual Studio, todas as seguintes etapas e rotinas contínuas ocorrem no nível do programa:

- Definindo a próxima instrução, ou seja, definindo seu computador para a próxima instrução a ser executada em um ambiente de quadro específico

- Executando, isto é, continuar a sair do modo de pisar

- Indo para a próxima instrução

- Continuando com o modo de revisão atual

- Suspensão dos fios contidos pelo programa

- Retomando os segmentos contidos pelo programa

> [!NOTE]
> A visualização da pilha de chamadas é implementada no nível de segmento. Para enumerar as informações do quadro ao visualizar a pilha de chamadas para um segmento, você deve implementar todos os métodos da interface [IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Métodos de controle do programa
 A tabela a seguir mostra os métodos do [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que devem ser implementados para um mecanismo de depuração minimamente funcional (DE) e controle de execução.

|Método|Descrição|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua executando todos os segmentos contidos por um programa de um estado parado. Necessário para o controle de execução.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua executando todos os segmentos contidos por um programa de um estado parado. Necessário para o controle de execução.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Executa um passo no fio dado. Continua executando todos os outros tópicos contidos pelo programa. Necessário para o controle de execução.|

 Para programas multithreaded, você também deve implementar o método [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) e todos os métodos da interface [IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Confira também
- [Controle de execução e avaliação do estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
