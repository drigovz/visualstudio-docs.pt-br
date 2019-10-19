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
ms.openlocfilehash: 401eb759523ed1a33d24c3a298db0b3de2b7d5a7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575872"
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
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Obtém o título anexado à enumeração para identificação.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)