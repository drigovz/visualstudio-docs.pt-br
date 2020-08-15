---
title: Enumeração SCRIPTTRACEINFO | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf4933cc5778dd4af21e1b12d64fc59d371ad097
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238212"
---
# <a name="scripttraceinfo-enumeration"></a>Enumeração SCRIPTTRACEINFO
Representa o evento de script que está sendo rastreado. Usado no [método IActiveScriptSiteTraceInfo:: SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|Valor|Evento de script|  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|O início de um script.|  
|SCRIPTTRACEINFO_SCRIPTEND|O final do script.|  
|SCRIPTTRACEINFO_COMCALLSTART|O início de uma chamada COM.|  
|SCRIPTTRACEINFO_COMCALLEND|O fim de uma chamada COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|O início da criação do objeto.|  
|SCRIPTTRACEINFO_CREATEOBJEND|O fim da criação do objeto.|  
|SCRIPTTRACEINFO_GETOBJSTART|O início de uma chamada GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|O fim de uma chamada GetObject.|