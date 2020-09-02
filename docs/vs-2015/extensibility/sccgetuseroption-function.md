---
title: Função SccGetUserOption | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd00a2b669b806b09a6ae221b2ba2e03f8d45ceb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200080"
---
# <a name="sccgetuseroption-function"></a>Função SccGetUserOption
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função recupera uma variedade de opções específicas do usuário.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 no O ponteiro de contexto do plug-in de controle do código-fonte.  
  
 nOption  
 no Opção para recuperar (consulte comentários para as opções possíveis).  
  
 lpVal  
 fora Valor associado à opção.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|A opção foi recuperada com êxito.|  
|SCC_E_OPNOTSUPPORTED|Não há suporte para a opção.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado.|  
  
## <a name="remarks"></a>Comentários  
 As opções a seguir são suportadas por este comando:  
  
|Opção de usuário|Descrição|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Determina se o usuário deseja fazer check-out da versão local dos arquivos. `lpVal` é atribuído `SCC_USEROPT_COLV_YES` (o usuário deseja fazer check-out de arquivos locais) ou `SCC_USEROPT_COLV_NO` .|  
  
## <a name="see-also"></a>Consulte Também  
 [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de Erro](../extensibility/error-codes.md)
