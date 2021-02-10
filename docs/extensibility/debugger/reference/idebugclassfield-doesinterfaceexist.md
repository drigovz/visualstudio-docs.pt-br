---
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3b7116b9e675605863805fb413340ea8b45ec608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947106"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Determina se uma interface específica está definida na classe.

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

## <a name="parameters"></a>Parâmetros
`pszInterfaceName`\
no Uma cadeia de caracteres que contém o nome da interface a ser procurada.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK, retornará S_FALSE se a interface não existir; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método em vigor Obtém uma enumeração de todas as interfaces e procura uma interface correspondente na lista.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
