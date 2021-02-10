---
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1893ffac03aba345589274475f81abd44b5b7b5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936815"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Obtém o `this` `Me` ponteiro (no [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) do objeto que contém o método.

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
fora Retorna um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa o ponteiro "This".

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Em linguagens orientadas a objeto, normalmente há um ponteiro implícito para a instanciação atual de uma classe. Isso é conhecido como `this` em C#/c + + e como `Me` no [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Confira também
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
