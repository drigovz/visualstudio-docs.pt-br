---
title: IDebugModuleLoadEvent2:GetModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726730"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
Fica com o módulo que está sendo carregado ou descarregado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>parâmetros
`pModule`\
[fora] Retorna um objeto [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) que representa o módulo que está carregando ou descarregando.

`pbstrDebugMessage`\
[dentro, fora] Retorna uma mensagem opcional descrevendo este evento. Se este parâmetro for um valor nulo, nenhuma mensagem será solicitada.

`pbLoad`\
[dentro, fora] Não zero`TRUE`( ) se o`FALSE`módulo estiver carregando e zero ( ) se o módulo estiver descarregando. Se este parâmetro for um valor nulo, nenhum status será solicitado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
