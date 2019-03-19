---
title: Enumeração APPBREAKFLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0862e6fc670be6cd3d3ca9fbf67f453aa0772a90
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158978"
---
# <a name="appbreakflags-enumeration"></a>Enumeração APPBREAKFLAGS
Indica o estado atual da depuração para aplicativos e threads.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|Mecanismo de linguagem deve ser interrompido imediatamente em todos os threads com BREAKREASON_DEBUGGER_BLOCK.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|Mecanismo de linguagem deve ser interrompido imediatamente com BREAKREASON_DEBUGGER_HALT.|  
|APPBREAKFLAG_STEP|0x00010000|Mecanismo de linguagem deve ser interrompido imediatamente no thread de passo a passo com BREAKREASON_STEP.|  
|APPBREAKFLAG_NESTED|0x00020000|O aplicativo está em execução aninhada em um ponto de interrupção.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|O depurador é depuração no nível do código-fonte.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|O depurador é depuração no nível do código de bytes.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|O depurador é depuração no nível do computador.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|Máscara para fatorar os tipos de etapa.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|Um ponto de interrupção está em andamento.|  
  
## <a name="remarks"></a>Comentários  
 Alguns sinalizadores de especificam que mecanismos de linguagem devem ser interrompido na próxima oportunidade, enquanto outros sinalizadores de especificam o modo de passo a passo do depurador.  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas, enumerações e constantes do depurador de Script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON Enumeration](../../winscript/reference/breakreason-enumeration.md)