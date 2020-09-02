---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728760"
---
# <a name="idebugfield"></a>IDebugField
Essa interface representa um campo, ou seja, uma descrição de um símbolo ou tipo.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolo implementa essa interface como a classe base para todos os campos.

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é a classe base para todos os campos. Com base no valor de retorno de [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md), essa interface pode retornar interfaces mais especializadas usando [QueryInterface](/cpp/atl/queryinterface). Além disso, muitas interfaces retornam `IDebugField` objetos de vários métodos.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IDebugField` .

|Método|Descrição|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtém informações de exibição sobre o símbolo ou tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtém o tipo de campo.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtém o tipo de campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtém o contêiner do campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtém o endereço do campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtém o tamanho de um campo, em bytes.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtém informações estendidas sobre um campo.|
|[Igual](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dois campos.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtém informações independentes de tipo sobre o símbolo ou tipo.|

## <a name="remarks"></a>Comentários
 Um tipo é equivalente a uma linguagem C `typedef` .

 No exemplo de linguagem C++ a seguir, `weather` é um tipo de classe e `sunny` e `stormy` são símbolos:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Se um campo representa um símbolo ou tipo pode ser determinado chamando [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) e examinando o resultado de [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) . Se o `FIELD_KIND_TYPE` bit for definido, o campo será um tipo e, se o `FIELD_KIND_SYMBOL` bit for definido, ele será um símbolo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
