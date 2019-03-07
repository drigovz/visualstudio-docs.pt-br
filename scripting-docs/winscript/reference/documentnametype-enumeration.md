---
title: Enumeração DOCUMENTNAMETYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 31e304cfbb0ed7cd19b832d7ed7c33ccc2c930c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094764"
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