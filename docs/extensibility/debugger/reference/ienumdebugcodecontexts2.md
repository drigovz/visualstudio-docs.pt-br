---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717275"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Esta interface enumera os contextos de código associados à sessão de depuração, ou com um determinado programa ou documento.

## <a name="syntax"></a>Sintaxe

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para representar uma lista de contextos de código para uma posição de texto específica em um programa ou uma lista de contextos de código para um determinado contexto de documento.

## <a name="notes-for-callers"></a>Observações para chamadores
 Ligue para [enumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para obter essa interface representando uma lista de contextos de código para uma posição de texto específica no documento de origem de um programa.

 Ligue para [enumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) para obter esta interface representando uma lista de todos os contextos de código em um documento de origem específico.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugCodeContexts2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera um número especificado de contextos de código em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Salta um número especificado de contextos de código em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtém o número de contextos de código em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio chama [o EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) para preencher uma lista de contextos de código que o usuário pode escolher ao definir a próxima declaração ou mostrar a desmontagem de um arquivo de origem. Vários contextos de código podem ocorrer, por exemplo, quando há várias instâncias de um modelo de estilo C++.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
