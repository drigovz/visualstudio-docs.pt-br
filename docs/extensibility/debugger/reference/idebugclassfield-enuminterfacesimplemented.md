---
title: IDebugClassField::EnumInterfacesImplementado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734493"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Cria um enumerador para as interfaces implementadas por esta classe.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>parâmetros
`ppEnum`\
[fora] Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) representando a lista de interfaces implementadas. Retorna um valor nulo se não houver interfaces.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna S_OK ou retorna S_FALSE se não houver interfaces implementadas nesta classe. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Cada elemento da enumeração é um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) descrevendo uma interface. Observe que o [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] código não gerenciado não usa interfaces como uma entidade discreta, de [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] modo que este método sempre retorna um valor nulo para código não gerenciado.

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
