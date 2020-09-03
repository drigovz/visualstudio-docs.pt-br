---
title: 'IDebugProgramHost2:: GetHostMachineName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramHost2::GetHostMachineName
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3e134a4e766583c8996c01cb02789202b819bd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722309"
---
# <a name="idebugprogramhost2gethostmachinename"></a>IDebugProgramHost2::GetHostMachineName
Obtém o nome do computador no qual o processo que hospeda este programa está sendo executado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetHostMachineName( 
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName( 
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parâmetros
`pbstrHostMachineName`\
fora Retorna o nome da máquina.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)
