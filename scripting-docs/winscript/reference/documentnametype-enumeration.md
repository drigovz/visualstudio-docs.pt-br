---
title: Enumeração DOCUMENTNAMETYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ee258602c47951f4731dc1378542cc83d57d72b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955205"
---
# <a name="documentnametype-enumeration"></a>Enumeração DOCUMENTNAMETYPE
Descreve os tipos para se obter um documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Obtém o nome como ele aparece na árvore do aplicativo.|  
|DOCUMENTNAMETYPE_TITLE|Obtém o nome como ele aparece na barra de título do visualizador.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Obtém o nome do arquivo sem um caminho.|  
|DOCUMENTNAMETYPE_URL|Obtém a URL do documento.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Obtém o título acrescentado com a enumeração para identificação.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)