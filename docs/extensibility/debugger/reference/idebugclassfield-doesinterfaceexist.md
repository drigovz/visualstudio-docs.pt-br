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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba732b698f7372772142fda73e71d9e22aa443a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734502"
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

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK, retornará S_FALSE se a interface não existir; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método em vigor Obtém uma enumeração de todas as interfaces e procura uma interface correspondente na lista.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
