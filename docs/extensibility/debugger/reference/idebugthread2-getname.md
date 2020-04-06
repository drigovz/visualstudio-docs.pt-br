---
title: IDebugThread2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718766"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Fica com o nome de um fio.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>parâmetros
`pbstrName`\
[fora] Retorna o nome do segmento.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O nome recuperado é sempre um nome que pode ser exibido e este nome descreve o segmento. O nome do segmento pode ser derivado de uma arquitetura de tempo de execução que suporta threads nomeados, ou pode ser um nome derivado do mecanismo de depuração. Alternativamente, o nome do segmento pode ser definido por uma chamada para o método [SetThreadName.](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
