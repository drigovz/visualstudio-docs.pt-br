---
title: Função SccQueryChanges | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: baa6059a1668be5507994921cb96ac3ed1cfd5fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200010"
---
# <a name="sccquerychanges-function"></a>Função SccQueryChanges
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função enumera uma determinada lista de arquivos, fornecendo informações sobre alterações de nome para cada arquivo por meio de uma função de retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccQueryChanges(  
   LPVOID           pContext,  
   LONG             nFiles,  
   LPCSTR*          lpFileNames,  
   QUERYCHANGESFUNC pfnCallback,  
   LPVOID           pvCallerData  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 no O ponteiro de contexto do plug-in de controle do código-fonte.  
  
 nFiles  
 no Número de arquivos na `lpFileNames` matriz.  
  
 lpFileNames  
 no Matriz de nomes de arquivo para obter informações.  
  
 pfnCallback  
 no Função de retorno de chamada para chamar cada nome de arquivo na lista (consulte [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obter detalhes).  
  
 pvCallerData  
 no Valor que será passado inalterado para a função de retorno de chamada.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|O processo de consulta foi concluído com êxito.|  
|SCC_E_PROJNOTOPEN|O projeto não foi aberto no controle do código-fonte.|  
|SCC_E_ACCESSFAILURE|Houve um problema ao acessar o sistema de controle do código-fonte, provavelmente devido a problemas de rede ou de contenção.|  
|SCC_E_NONSPECIFICERROR|Ocorreu um erro não especificado ou geral.|  
  
## <a name="remarks"></a>Comentários  
 As alterações que estão sendo consultadas são para o namespace: especificamente, renomear, adicionar e remover um arquivo.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)   
 [Códigos de Erro](../extensibility/error-codes.md)
