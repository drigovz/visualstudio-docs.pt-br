---
title: Métodos relacionados a pontos de ruptura | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739201"
---
# <a name="breakpoint-related-methods"></a>Métodos relacionados a pontos de ruptura
Um mecanismo de depuração (DE) deve suportar a configuração de pontos de interrupção. A depuração do Visual Studio suporta os seguintes tipos de pontos de interrupção:

- Bound

     Solicitado através da ui e vinculado com sucesso a um local de código especificado

- Pendente

     Solicitado através da UI, mas ainda não vinculado a instruções reais

## <a name="discussion"></a>Discussão
 Por exemplo, um ponto de ruptura pendente ocorre quando as instruções ainda não estão carregadas. Quando o código é carregado, os pontos de interrupção pendentes tentam vincular-se ao código no local prescrito, ou seja, inserir instruções de quebra no código. Os eventos são enviados ao Gerenciador de depuração de sessão (SDM) para indicar a vinculação bem sucedida ou notificar que houve erros de vinculação.

 Um ponto de interrupção pendente também gerencia sua própria lista interna de pontos de interrupção vinculados correspondentes. Um ponto de interrupção pendente pode causar a inserção de muitos pontos de interrupção no código. A ui de depuração do Visual Studio mostra uma visão de árvore de pontos de interrupção pendentes e seus pontos de interrupção vinculados correspondentes.

 A criação e o uso de pontos de interrupção pendentes exigem a implementação do método [IDebugEngine2::CreatePendingBreakpoint,](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) bem como os seguintes métodos de interfaces [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

|Método|Descrição|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Determina se um ponto de ruptura pendente especificado pode se vincular a um local de código.|
|[Associar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Vincula um ponto de ruptura pendente especificado a um ou mais locais de código.|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Fica com o estado de um ponto de ruptura pendente.|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Obtém o pedido de ponto de ruptura usado para criar um ponto de ruptura pendente.|
|[Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Alterna o estado habilitado de um ponto de ruptura pendente.|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Enumera todos os breakpoints vinculados a um ponto de interrupção pendente.|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Enumera todos os pontos de interrupção de erro que resultam de um breakpoint pendente.|
|[Excluir](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Exclui um ponto de interrupção pendente e todos os pontos de interrupção vinculados a ele.|

 Para enumerar os pontos de interrupção e os pontos de interrupção de erro, você deve implementar todos os métodos do [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) e do [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md).

 Pontos de interrupção pendentes que se ligam a um local de código exigem a implementação dos seguintes métodos [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

|Método|Descrição|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de ruptura pendente que contém um ponto de ruptura.|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtém o estado de um ponto de ruptura.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de ponto de ruptura que descreve um ponto de ruptura.|
|[Habilitar](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Ativa ou desativa um ponto de ruptura.|
|[Excluir](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Exclui um ponto de ruptura vinculado.|

 As informações de resolução e solicitação requerem a implementação dos seguintes métodos [IDebugBreakpointResolution2.](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)

|Método|Descrição|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Obtém o tipo de ponto de ruptura representado por uma resolução.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Obtém as informações de resolução de ponto de ruptura que descrevem um ponto de ruptura.|

 A resolução de erros que podem ocorrer durante a vinculação requer a implementação dos seguintes métodos [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

|Método|Descrição|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de ruptura pendente que contém um ponto de ruptura de erro.|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de erro de ponto de ruptura que descreve um ponto de ruptura de erro.|

 A resolução de erros que podem ocorrer durante a vinculação também requer os seguintes métodos de [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md).

|Método|Descrição|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Tem o tipo de ponto de ruptura.|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Obtém as informações de resolução de um ponto de ruptura.|

 A visualização do código-fonte em um ponto de ruptura requer que você implemente os métodos do [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) e/ou os métodos do [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md).

## <a name="see-also"></a>Confira também
- [Controle de execução e avaliação do estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
