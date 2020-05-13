---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9930f8ecf0c2f9b6fff4ce1c9e3edb935c5a7912
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730676"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Este método informa o mecanismo de depuração sobre as informações do estado JustMyCode.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetJustMyCodeState(
   BOOL           fUpdate,
   DWORD          dwModules,
   JMC_CODE_SPEC* rgJMCSpec
);
```

```csharp
int SetJustMyCodeState(
   int             fUpdate,
   uint            dwModules,
   JMC_CODE_SPEC[] rgJMCSpec
);
```

## <a name="parameters"></a>parâmetros
`fUpdate`\
[em] Não zero`TRUE`( ) para atualizar`FALSE`as informações atuais, zero ( ) para redefinir todas as informações (ignorando qualquer coisa previamente definida).

`dwModules`\
[em] Número de estruturas de informação em`rgJMCSpec.`

`rgJMCSpec`\
[em] Matriz [de](../../../extensibility/debugger/reference/jmc-code-spec.md) JMC_CODE_SPEC estruturas para usar.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
 JustMyCode é o conceito de depurar apenas o código que pertence a um usuário e ignorar todos os códigos intermediários, como o código do sistema — mesmo que o código-fonte esteja disponível para esse código do sistema.

## <a name="see-also"></a>Confira também
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
