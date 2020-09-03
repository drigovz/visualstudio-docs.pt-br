---
title: Função SccAddFilesFromSCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d5af748c9180644cae928d1b6db3a3f880b6b286
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200914"
---
# <a name="sccaddfilesfromscc-function"></a>Função SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função adiciona uma lista de arquivos do controle do código-fonte ao projeto atualmente aberto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 no O ponteiro de contexto do plug-in de controle do código-fonte.  
  
 hWnd  
 no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.  
  
 lpUser  
 [entrada, saída] O nome de usuário (até SCC_USER_SIZE, incluindo o terminador nulo).  
  
 lpAuxProjPath  
 [entrada, saída] Cadeia de caracteres auxiliar que identifica o projeto (até `SCC_PRJPATH_` o tamanho, incluindo o terminador nulo).  
  
 recfiles  
 no Número de arquivos fornecidos pelo `lpFilePaths` .  
  
 lpFilePaths  
 [entrada, saída] Matriz de nomes de arquivos a serem adicionados ao projeto atual.  
  
 lpDestination  
 no O caminho de destino onde os arquivos devem ser gravados.  
  
 lpComment  
 no O comentário a ser aplicado a cada um dos arquivos que estão sendo adicionados.  
  
 pbResults  
 [entrada, saída] Matriz de sinalizadores que são definidos para indicar êxito (diferente de zero ou verdadeiro) ou falha (zero ou falso) para cada arquivo (o tamanho da matriz deve ser pelo menos `cFiles` longo).  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|O projeto não está aberto.|  
|SCC_E_OPNOTPERFORMED|A conexão não é do mesmo projeto especificado por `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|O usuário não está autorizado a atualizar o banco de dados.|  
|SCC_E_NONSPECIFICERROR|Erro desconhecido.|  
|SCC_I_RELOADFILE|Um arquivo ou projeto precisa ser recarregado.|  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
