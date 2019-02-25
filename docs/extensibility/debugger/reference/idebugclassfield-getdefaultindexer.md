---
title: IDebugClassField::GetDefaultIndexer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d884b8e066b539b925e50d4f49f65168ca6156c0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723559"
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

#### <a name="parameters"></a>Parâmetros
 `pbstrIndexer`

 [out] Retorna uma cadeia de caracteres que contém o nome do indexador padrão.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum indexador padrão. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 O indexador padrão de uma classe é a propriedade que está marcada como o `Default` propriedade para acessos de matriz. Isso é específico para [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]. Aqui está um exemplo de um indexador padrão declarado no [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] e como ele é usado.

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

## <a name="see-also"></a>Consulte também
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)