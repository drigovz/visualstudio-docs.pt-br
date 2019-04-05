---
title: Função SccGetVersion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4e548f1f2b82a97206cdf41174a8c1c7d61e885
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923479"
---
# <a name="sccgetversion-function"></a>Função SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função obtém o número de versão de API de plug-in de controle de origem compatível com o plug-in de controle de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
