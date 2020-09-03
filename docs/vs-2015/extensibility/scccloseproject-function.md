---
title: Função SccCloseProject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d2364215f528f16d05ecf0c53b152f7334f4b4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156142"
---
# <a name="scccloseproject-function"></a>Função SccCloseProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função fecha um projeto, marcando o final de uma sessão específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pvContext  
 A estrutura de contexto do plug-in de controle do código-fonte.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O projeto foi fechado com êxito.|  
|SCC_E_PROJNOTOPEN|Nenhum projeto está aberto no momento.|  
|SCC_E_NOTAUTHORIZED|O usuário não tem permissão para executar esta operação.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 O [SccOpenProject](../extensibility/sccopenproject-function.md) é sempre chamado antes dessa função. Uma chamada para essa função é seguida por uma chamada para a `SccOpenProject` função ou [SccUninitialize](../extensibility/sccuninitialize-function.md), que termina a conexão com o sistema de controle do código-fonte completamente.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
