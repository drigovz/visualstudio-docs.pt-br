---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2819724c204631112fd1a3e827126c4bc176972
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721048"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Esta interface fornece suporte para:

- Recuperando uma seqüência arbitrariamente longa associada à propriedade.

- Associando uma identificação única com a propriedade.

- Recuperando uma lista de espectadores personalizados para a propriedade.

- Definir o valor de uma propriedade com a capacidade de relatar quaisquer erros resultantes

## <a name="syntax"></a>Sintaxe

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface no mesmo objeto que implementa o [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) para fornecer suporte para strings longas, IDs de propriedade e visualizadores personalizados.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para o `IDebugProperty2` [QueryInterface](/cpp/atl/queryinterface) em uma interface para obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos `IDebugProperty2`herdados, `IDebugProperty3` a interface expõe os seguintes métodos.

|Método|Descrição|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Retorna o comprimento da string associada à propriedade.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Retorna a seqüência em um buffer fornecido pelo usuário.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Cria uma identificação única para esta propriedade.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Destrói a identificação única desta propriedade.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Retorna o número de espectadores personalizados com os que esta propriedade pode ser visualizada.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Retorna a lista de espectadores personalizados com os que esta propriedade pode ser visualizada.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Define o valor desta propriedade, retornando uma mensagem de erro se algo der errado.|

## <a name="remarks"></a>Comentários
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) é a maneira preferida para o SDM (Session Debug Manager, gerente de depuração de sessão) definir o valor de um imóvel.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
