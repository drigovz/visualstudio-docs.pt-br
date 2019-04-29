---
title: Enumeração SCRIPTLANGUAGEVERSION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aab63989d1ae02f7c75fc9c20a14d59e8a05078
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840196"
---
# <a name="scriptlanguageversion-enumeration"></a>Enumeração SCRIPTLANGUAGEVERSION
Especifica os possíveis versões de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|A versão padrão. O valor inteiro é 0.|  
|SCRIPTLANGUAGEVERSION_5_7|A versão 5.7 de script do Windows. O valor inteiro é 1.|  
|SCRIPTLANGUAGEVERSION_5_8|A versão 5.8 de script do Windows. O valor inteiro é 2.|  
|SCRIPTLANGUAGEVERSION_MAX|A versão máxima. O valor inteiro é 255.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)