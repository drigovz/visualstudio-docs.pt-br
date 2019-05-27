---
title: IDebugSettingsCallback2::EnumEEs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5205cfbda0420e45fc1e22dac678d97975f937a8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212159"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Enumera os avaliadores de expressão disponível considerando os identificadores de idioma e o fornecedor.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parâmetros
`celtBuffer`\
[in] Número de elementos no `pceltEEs` buffer.

`rgguidLang`\
[no, out] Identificador exclusivo para a linguagem de programação.

`rgguidVendor`\
[no, out] Identificador exclusivo para o fornecedor.

`pceltEEs`\
[no, out] Matriz de avaliadores de expressão.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)