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
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574372"
---
# <a name="scriptlanguageversion-enumeration"></a>Enumeração SCRIPTLANGUAGEVERSION
Especifica as versões de script possíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|A versão padrão. O valor inteiro é 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows scripting versão 5,7. O valor inteiro é 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows scripting versão 5,8. O valor inteiro é 2.|  
|SCRIPTLANGUAGEVERSION_MAX|A versão máxima. O valor inteiro é 255.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)