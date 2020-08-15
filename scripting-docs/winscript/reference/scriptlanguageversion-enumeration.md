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
ms.openlocfilehash: 511bc3525480306e0fe3075231c1e55794f01e9e
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238680"
---
# <a name="scriptlanguageversion-enumeration"></a>Enumeração SCRIPTLANGUAGEVERSION
Especifica as versões de script possíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|Valor|Versão de script|  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|A versão padrão. O valor inteiro é 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows scripting versão 5,7. O valor inteiro é 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows scripting versão 5,8. O valor inteiro é 2.|  
|SCRIPTLANGUAGEVERSION_MAX|A versão máxima. O valor inteiro é 255.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)