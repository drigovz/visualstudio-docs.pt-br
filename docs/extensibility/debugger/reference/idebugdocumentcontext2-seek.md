---
title: IDebugDocumentContext2::Seek | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f001eb73e3c24ac1c9f15a4bd2c37c8d2cbe660e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56709519"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Move o contexto do documento por um determinado número de instruções ou linhas.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

#### <a name="parameters"></a>Parâmetros
 `nCount`

 [in] O número de instruções ou linhas para seguir em frente, dependendo do contexto de documento.

 `ppDocContext`

 [out] Retorna um novo [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objeto com a nova posição.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)