---
title: IDebugProviderProgramNode2:DemarshalDebuggeeInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720709"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Obtém uma interface especificada entre os limites do processo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>parâmetros
`riid`\
[em] GUID da interface para obter.

`ppvObject`\
[fora] Retorna o objeto que implementa a interface desejada. [C++] isso pode ser lançado diretamente para o tipo de interface desejado. [C#] use <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> o método para obter a interface desejada.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é usado quando o motor [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de depuração está funcionando no espaço de processo e o programa que está sendo depurado está sendo executado em seu próprio espaço de processo.

## <a name="see-also"></a>Confira também
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
