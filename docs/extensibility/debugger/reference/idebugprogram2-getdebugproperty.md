---
title: IDebugProgram2::GetDebugProperty | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722887"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Fica com as propriedades do programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>parâmetros
`ppProperty`\
[fora] Retorna um objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa as propriedades do programa.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 As propriedades devolvidas por este método são específicas do programa. Se o programa precisar devolver mais de uma propriedade, então o objeto [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) devolvido por este método é um contêiner de propriedades adicionais e chamar o método [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) retorna uma lista de todas as propriedades.

 Um programa pode expor qualquer número e tipo de `IDebugProperty2` propriedades adicionais que possam ser descritas através da interface. Um IDE pode exibir as propriedades adicionais do programa através de uma interface de usuário de navegador de propriedade genérica.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
