---
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3e88f209b506d8baf10a779d282a78122c274fb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211931"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtém o `this` (`Me` em [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) ponteiro do objeto que contém o método.

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

## <a name="parameters"></a>Parâmetros
`ppClass`\
[out] Retorna um [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) objeto que representa o ponteiro "this".

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Em linguagens orientadas a objeto, normalmente há um ponteiro implícito para a instanciação atual de uma classe. Isso é conhecido como `this` em C#/C++ e como `Me` na [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Consulte também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)