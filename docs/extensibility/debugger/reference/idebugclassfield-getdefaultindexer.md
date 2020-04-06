---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57e00107374485043af370967794bdade1c213d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734426"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
Obtém o nome do indexador padrão.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetDefaultIndexer( 
   BSTR* pbstrIndexer
);
```

```csharp
int GetDefaultIndexer(
   out string pbstrIndexer
);
```

## <a name="parameters"></a>parâmetros
`pbstrIndexer`[fora] Retorna uma seqüência contendo o nome do indexador padrão.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna S_OK ou retorna S_FALSE se não houver indexador padrão. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O indexador padrão de uma classe é `Default` a propriedade marcada como a propriedade para acessos de matriz. Isso é [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]específico para. Aqui está um exemplo de um [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] indexador padrão declarado e como ele é usado.

```vb
Imports System.Collections;

Public Class Class1
    Private myList as Hashtable

    Default Public Property Item(ByVal Index As Integer) As Integer
        Get
            Return CType(List(Index), Integer)
        End Get
        Set(ByVal Value As Integer)
            List(Index) = Value
        End Set
    End Property
End Class

Function GetItem(Index as Integer) as Integer
    Dim classList as Class1 = new Class1
    Dim value as Integer

    ' Access array through default indexer
    value = classList(2)

    ' Access array through explicit property
    value = classList.Item(2)

    Return value
End Function
```

## <a name="see-also"></a>Confira também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
