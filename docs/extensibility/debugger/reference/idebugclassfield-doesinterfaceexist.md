---
title: IDebugClassField::DoesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7884bff62321ed07c3a11a6db65855b1edea0adc
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688401"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina se uma interface específica é definida na classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

#### <a name="parameters"></a>Parâmetros
 `pszInterfaceName`

 [in] Uma cadeia de caracteres que contém o nome da interface a ser procurado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK, retorna S_FALSE se a interface não existir; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Em vigor, esse método obtém uma enumeração de todas as interfaces e pesquisa a lista para uma interface correspondente.

## <a name="see-also"></a>Consulte também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)