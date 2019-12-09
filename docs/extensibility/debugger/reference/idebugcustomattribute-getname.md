---
title: IDebugCustomAttribute::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3ed7abc9682d0a9f56c50fe7510ed3f276a6bf5a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315202"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Obtém o nome do atributo personalizado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parâmetros
`bstrName`\
[out] Retorna uma cadeia de caracteres que contém o nome do atributo personalizado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Nomeado retornado por esse método corresponde ao nome da classe usada para declarar o atributo. Não exatamente, isso pode corresponder ao nome da classe de atributo personalizado em si como o c# permite que o sufixo "Attribute" a ser removido de um nome de atributo personalizado quando ele é usado em uma declaração.

## <a name="see-also"></a>Consulte também
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)