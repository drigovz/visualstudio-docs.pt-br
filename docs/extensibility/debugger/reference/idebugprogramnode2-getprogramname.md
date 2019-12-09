---
title: IDebugProgramNode2::GetProgramName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetProgramName
helpviewer_keywords:
- IDebugProgramNode2::GetProgramName
ms.assetid: 510c7f5d-48ff-4d9f-ad79-fbad9f15239d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9882bd1686498bd9d1afc27f3a7edb695226a2f7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351101"
---
# <a name="idebugprogramnode2getprogramname"></a>IDebugProgramNode2::GetProgramName
Obtém o nome do programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetProgramName (
    BSTR* pbstrProgramName
);
```

```csharp
int GetProgramName (
    out string pbstrProgramName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrProgramName`\
[out] Retorna o nome do programa.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
O nome de um programa não é a mesma coisa que o caminho para o programa, embora o nome do programa pode ser parte de um caminho.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto que implementa o [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interface. O `MakeBstr` função aloca uma cópia da cadeia de caracteres especificada como um BSTR.

```cpp
HRESULT CProgram::GetProgramName(BSTR* pbstrProgramName) {
    if (!pbstrProgramName)
        return E_INVALIDARG;

    // Assign the member program name to the passed program name.
    *pbstrProgramName = MakeBstr(m_pszProgramName);
    return NOERROR;
}
```

## <a name="see-also"></a>Consulte também
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
