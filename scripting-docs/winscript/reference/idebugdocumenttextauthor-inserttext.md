---
title: 'IDebugDocumentTextAuthor:: InsertText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.InsertText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::InsertText
ms.assetid: ef4e6a5b-8efa-4290-b498-c0f8a6aac09b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad927f417c44b471a3fcee96695a1109d33ed17e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572071"
---
# <a name="idebugdocumenttextauthorinserttext"></a>IDebugDocumentTextAuthor::InsertText
Insere um novo texto no documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT InsertText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToInsert,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cCharacterPosition`  
 no Local para inserir o texto.  
  
 `cNumToInsert`  
 no Número de caracteres a serem inseridos.  
  
 `pcharText[]`  
 no Um buffer que contém os caracteres a serem inseridos.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método insere o novo texto no documento.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
 [IDebugDocumentTextAuthor::RemoveText](../../winscript/reference/idebugdocumenttextauthor-removetext.md)