---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 979ca1b0422cf3a333164570aec0a0b0dee39960
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693640"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Essa interface representa um processo em execução e seus programas. Essa interface existe como uma substituição para vários métodos na [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface. Ele fornece controle sobre todos os programas no processo.

> [!NOTE]
>  [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md), e [etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md) métodos foram preteridos e não deve mais ser usados. Use os métodos correspondentes no `IDebugProcess3` interface em vez disso.

## <a name="syntax"></a>Sintaxe

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface é implementada por um fornecedor de porta personalizada para gerenciar os programas como um grupo. Quando os programas são gerenciados como um grupo, você pode controlar sua execução e estabelecer um idioma para um avaliador de expressão. Esta interface deve ser implementada pelo fornecedor de porta.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é chamada principalmente pelo Gerenciador de depuração de sessão (SDM) para interagir com um grupo de programas identificado nesse processo.

 Chame [QueryInterface](/cpp/atl/queryinterface) em um [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos herdados de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md), `IDebugProcess3` implementa os métodos a seguir.

|Método|Descrição|
|------------|-----------------|
|[Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Continua a execução de ou passando por um processo.|
|[Executar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Inicia a execução de um processo.|
|[Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Etapas de encaminham uma instrução ou instrução no processo.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Obtém o motivo que o processo foi iniciado para depuração.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Define o idioma de hospedagem para que o mecanismo de depuração possa carregar o avaliador de expressão apropriada.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Recupera o idioma definido atualmente para esse processo.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Desabilita editar e continuar (ENC) para esse processo.<br /><br /> Um fornecedor de porta personalizado não implementa esse método (ele deve sempre retornar `E_NOTIMPL`).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Obter o estado ENC para esse processo.<br /><br /> Um fornecedor de porta personalizado não implementa esse método (ele deve sempre retornar `E_NOTIMPL`).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Recupera uma matriz de identificadores exclusivos de mecanismos de depuração disponíveis.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)