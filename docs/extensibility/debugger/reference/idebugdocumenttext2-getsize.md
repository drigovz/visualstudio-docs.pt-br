---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9207858bd43809cbc070935ae2f53f354d9d6f9b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199165"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera o tamanho do texto nessa posição no documento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>Parâmetros
`pcNumLines`\
[out] Retorna o número de linhas de texto.

`pcNumChars`\
[out] Retorna o número de caracteres de texto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

 [C++ somente] Se um valor específico não for desejado, passe um valor nulo para o parâmetro.

 [C# somente] Ambos os parâmetros devem ser especificados.

## <a name="see-also"></a>Consulte também
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)