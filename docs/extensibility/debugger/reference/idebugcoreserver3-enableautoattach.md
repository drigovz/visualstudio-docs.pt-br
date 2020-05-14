---
title: IDebugCoreServer3:EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732915"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Permite a fixação automática dos motores de depuração especificados.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>parâmetros
`rgguidSpecificEngines`\
[em] Matriz de GUIDs para cada mecanismo de depuração para marcar como conexão automática.

`celtSpecificEngines`\
[em] O número de motores `rgguidSpecificEngines`especificados em .

`pszStartPageUrl`\
[em] A URL inicial para usar ao anexar automaticamente.

`pbstrSessionID`\
[fora] ID da sessão que foi anexada automaticamente.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro. Um código `E_AUTO_ATTACH_NOT_REGISTERED`de erro é , o que indica que a fábrica de classe de conexão automática não foi registrada.

## <a name="remarks"></a>Comentários
 Quando um programa associado à URL especificada é iniciado, os mecanismos de depuração especificados são automaticamente iniciados e conectados.

## <a name="see-also"></a>Confira também
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
