---
title: 'IRemoteDebugApplication:: ResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577456"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Continua um aplicativo que está atualmente em um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `prptFocus`  
 no Para modos de depuração, o thread que deve ser afetado pelo modo de revisão.  
  
 `bra`  
 no A ação a ser tomada na retomada do aplicativo.  
  
 `era`  
 no A ação a ser tomada no caso em que o aplicativo foi interrompido devido a um erro.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método continua um aplicativo que está atualmente em um ponto de interrupção.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 @No__t_1 de [Enumeração BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [ERRORRESUMEACTION Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)