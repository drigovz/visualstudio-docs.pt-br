---
title: 'IDebugAlias2:: getappdomainid | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9c50473e12399e3977de55e67c7251d5783eecfc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947119"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Recupera o identificador para o domínio do aplicativo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>Parâmetros
`pappDomainId`\
fora Retorna o identificador de domínio do aplicativo.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O identificador de domínio do aplicativo muda sempre que o aplicativo é reiniciado e um novo domínio de aplicativo é criado.

## <a name="see-also"></a>Confira também
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
