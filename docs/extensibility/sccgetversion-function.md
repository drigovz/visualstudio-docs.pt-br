---
title: Função SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe071cb0c0de62f4e59785f829adfaacc992336
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023532"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
Essa função obtém o número de versão de API de plug-in de controle de origem compatível com o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `LONG` tipo de dados que contém o número de versão de API de plug-in de controle de origem com suporte:  
  
|WORD|Descrição|  
|----------|-----------------|  
|HIWORD|Versão principal|  
|LOWORD|Versão secundária|  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, se um plug-in de controle de origem dá suporte à versão 1.3 da API de plug-in de controle de origem, essa função retornará 0x0103.  
  
## <a name="see-also"></a>Consulte também  
 [Funções de API do plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)