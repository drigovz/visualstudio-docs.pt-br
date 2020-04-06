---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721178"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Cria um ID exclusivo para esta propriedade para garantir que ela seja única entre todas as outras propriedades.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é chamado quando o gerenciador de depuração de sessão quer garantir que essa propriedade seja identificada exclusivamente entre todas as outras propriedades. O mecanismo de depuração (DE) suporta este método, a menos que as propriedades com as que ele lida já sejam identificadas exclusivamente. Se o DE não suportar este `E_NOTIMPL`método, ele retorna .

 Qualquer ID único `CreateObjectID` criado com é destruído quando o método [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) é chamado; isso também sinaliza o fim da necessidade de identificar exclusivamente essa propriedade.

> [!NOTE]
> Não há nenhum método para recuperar este ID único, então o DE pode `CreateObjectID` fazer o que quiser para IDs únicos quando o método é chamado.

## <a name="see-also"></a>Confira também
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
