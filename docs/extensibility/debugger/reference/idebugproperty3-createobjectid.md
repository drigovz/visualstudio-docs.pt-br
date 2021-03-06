---
title: 'IDebugProperty3:: createobjectid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d555d7b0480d910a5cb88397db5bfd7e734fd1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896117"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Cria uma ID exclusiva para essa propriedade para garantir que ela seja exclusiva entre todas as outras propriedades.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado quando o Gerenciador de depuração de sessão deseja certificar-se de que essa propriedade seja identificada exclusivamente entre todas as outras propriedades. O mecanismo de depuração (DE) dá suporte a esse método, a menos que as propriedades com as quais ele lida já estejam identificadas exclusivamente. Se o DE não oferecer suporte a esse método, ele retornará `E_NOTIMPL` .

 Qualquer ID exclusiva criada com `CreateObjectID` é destruída quando o método [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) é chamado; isso também sinaliza o fim da necessidade de identificar exclusivamente essa propriedade.

> [!NOTE]
> Não há nenhum método para recuperar essa ID exclusiva, portanto, o DE pode fazer o que quiser para IDs exclusivas quando o `CreateObjectID` método é chamado.

## <a name="see-also"></a>Confira também
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
