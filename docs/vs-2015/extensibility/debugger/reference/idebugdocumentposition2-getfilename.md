---
title: IDebugDocumentPosition2::GetFileName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetFileName
helpviewer_keywords:
- IDebugDocumentPosition2::GetFileName
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8298388f9f7bd0504cf586241fbbf4945feebdd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200275"
---
# <a name="idebugdocumentposition2getfilename"></a>IDebugDocumentPosition2::GetFileName
Obtém o nome do arquivo do arquivo de origem que contém a posição do documento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetFileName( 
   BSTR* pbstrFileName
);
```

```csharp
int GetFileName( 
   out string pbstrFileName
);
```

#### <a name="parameters"></a>Parâmetros
 `pbstrFileName`

 [out] Retorna o nome do arquivo do arquivo de origem.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um arquivo de origem não pode ter sempre um nome de arquivo (o arquivo de origem pode não existir no disco, por exemplo).

## <a name="see-also"></a>Consulte também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)