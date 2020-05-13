---
title: IDebugDocumentText2:GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: edc4a209537ca4bd54d3f6d9343d1496ab7c0e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731583"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Recupera o tamanho do texto nesta posição no documento.

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

## <a name="parameters"></a>parâmetros
`pcNumLines`\
[fora] Retorna o número de linhas de texto.

`pcNumChars`\
[fora] Retorna o número de caracteres do texto.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários

 [Somente C++] Se um valor específico não for desejado, passe um NULL para o parâmetro.

 [C# apenas] Ambos os parâmetros devem ser especificados.

## <a name="see-also"></a>Confira também
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
