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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b997f3724dc3d1bb0f9155f3b575fef3ce9f2802
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879621"
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