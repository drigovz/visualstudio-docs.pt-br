---
title: Estrutura TEXT_DOCUMENT_ARRAY | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- TEXT_DOCUMENT_ARRAY Structure
ms.assetid: 47c08f23-981b-4105-9240-6dfffc6cb91b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d188729b68f8086da62d40ca28fc29945c8be7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840051"
---
# <a name="textdocumentarray-structure"></a>Estrutura TEXT_DOCUMENT_ARRAY
Uma matriz de [IDebugDocumentText Interface](../../winscript/reference/idebugdocumenttext-interface.md) objetos. Os membros são alocados com CoTaskMemAlloc.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct tagTEXT_DOCUMENT_ARRAY{    DWORD dwCount;    [size_is(dwCount)] IDebugDocumentText **Members;} TEXT_DOCUMENT_ARRAY;  
```  
  
## <a name="members"></a>Membros  
 `dwCount`  
 O número de documentos.  
  
 `Members`  
 O conjunto de documentos.  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)