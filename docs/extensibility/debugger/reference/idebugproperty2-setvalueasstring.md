---
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 112ded163f38b93e9918387d8ca6beafb8282647
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721245"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Define o valor de uma propriedade a partir de uma determinada seqüência.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>parâmetros
`pszValue`\
[em] Uma seqüência contendo o valor a ser definido.

`nRadix`\
[em] Um rádio para ser usado na interpretação de qualquer informação numérica. Isso pode ser 0 para tentar determinar o radix automaticamente.

`dwTimeout`\
[em] Especifica o tempo máximo, em milissegundos, para esperar antes de retornar deste método. Use `INFINITE` para esperar indefinidamente.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro. A tabela a seguir mostra outros valores possíveis.

|Valor|Descrição|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|A seqüência não pôde ser convertida em um valor de propriedade, ou o valor da propriedade não pôde ser definido.|
|`E_SETVALUE_VALUE_IS_READONLY`|a propriedade é somente leitura.|

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
