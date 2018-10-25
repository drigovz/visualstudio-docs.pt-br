---
title: IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
helpviewer_keywords:
- IDebugDocumentPosition2::IsPositionInDocument
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 59f82337d2a599ee1ddbcd9737474951dd16e09b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890290"
---
# <a name="idebugdocumentposition2ispositionindocument"></a>IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Determina se a posição do documento está contida em um determinado documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```csharp  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pDoc`  
 [in] O [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) objeto que representa o recipiente candidato de documento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é usado principalmente em Configurar pontos de interrupção [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfaces. Como documentos são carregados, a posição do ponto de interrupção é chamada para determinar se o documento contém nessa posição.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)

