---
title: 'IDebugProperty2:: SetValueAsString | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721245"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Define o valor de uma propriedade de uma determinada cadeia de caracteres.

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

## <a name="parameters"></a>Parâmetros
`pszValue`\
no Uma cadeia de caracteres que contém o valor a ser definido.

`nRadix`\
no Uma Radix a ser usada na interpretação de qualquer informação numérica. Isso pode ser 0 para tentar determinar a base automaticamente.

`dwTimeout`\
no Especifica o tempo máximo, em milissegundos, a aguardar antes de retornar desse método. Use `INFINITE` para aguardar indefinidamente.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro. A tabela a seguir mostra outros valores possíveis.

|Valor|Descrição|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|A cadeia de caracteres não pôde ser convertida em um valor de propriedade ou o valor da propriedade não pôde ser definido.|
|`E_SETVALUE_VALUE_IS_READONLY`|a propriedade é somente leitura.|

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
