---
title: Constantes TEXT_DOC_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- TEXT_DOC_ATTR
apilocation:
- scrobj.dll
helpviewer_keywords:
- TEXT_DOC_ATTR constants
ms.assetid: fd9c53a4-8f73-4c6a-abe5-6b831ecd5b1e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e3fd21ba720dfed394e497a9a56a1bb6898dc60
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097247"
---
# <a name="textdocattr-constants"></a>Constantes TEXT_DOC_ATTR
Descrevem os atributos do documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef DWORD TEXT_DOC_ATTR;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|TEXT_DOC_ATTR_READONLY|0x00000001|O documento é somente leitura.|  
|TEXT_DOC_ATTR_TYPE_PRIMARY|0x00000002|O documento é o arquivo primário dessa árvore do documento.|  
|TEXT_DOC_ATTR_TYPE_WORKER|0x00000004|O documento é um trabalhador.|  
|TEXT_DOC_ATTR_TYPE_SCRIPT|0x00000008|O documento é um arquivo de script.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)