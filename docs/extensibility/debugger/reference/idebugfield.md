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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728760"
---
# <a name="idebugfield"></a>IDebugField
Esta interface representa um campo, ou seja, uma descrição de um símbolo ou tipo.

## <a name="syntax"></a>Sintaxe

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um provedor de símbolos implementa essa interface como a classe base para todos os campos.

## <a name="notes-for-callers"></a>Observações para chamadores
 Esta interface é a classe base para todos os campos. Com base no valor de retorno do [GetKind,](../../../extensibility/debugger/reference/idebugfield-getkind.md)esta interface pode retornar interfaces mais especializadas usando [o QueryInterface](/cpp/atl/queryinterface). Além disso, muitas `IDebugField` interfaces retornam objetos de vários métodos.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugField`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtém informações exibidas sobre o símbolo ou tipo.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Fica com o tipo de campo.|
|[Gettype](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Tem o tipo de campo.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Pega o recipiente do campo.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Pega o endereço do campo.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Fica do tamanho de um campo, em bytes.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtém informações estendidas sobre um campo.|
|[Igual](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dois campos.|
|[Gettypeinfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtém informações independentes sobre o símbolo ou tipo.|

## <a name="remarks"></a>Comentários
 Um tipo é equivalente `typedef`a uma língua C.

 No exemplo de linguagem C++, `weather` é `sunny` um `stormy` tipo de classe e são símbolos:

```cpp
class weather;
weather sunny;
weather stormy;
```

 Se um campo representa um símbolo ou tipo pode ser determinado ligando para [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) e examinando o [resultado FIELD_KIND.](../../../extensibility/debugger/reference/field-kind.md) Se `FIELD_KIND_TYPE` a broca estiver definida, o campo `FIELD_KIND_SYMBOL` é um tipo e, se a broca estiver definida, será um símbolo.

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
