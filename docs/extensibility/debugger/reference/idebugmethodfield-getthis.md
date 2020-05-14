---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727169"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtém `this` `Me` o [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]ponteiro (in) do objeto que contém o método.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>parâmetros
`ppClass`\
[fora] Retorna um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) representando o ponteiro "isso".

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Em linguagens orientadas a objetos, há tipicamente um ponteiro implícito para a instanciação atual de uma classe. Isso é `this` conhecido como em C#/C++ e como `Me` em [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Confira também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
