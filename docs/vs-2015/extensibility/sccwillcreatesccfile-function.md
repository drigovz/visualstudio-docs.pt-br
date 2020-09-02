---
title: Função SccWillCreateSccFile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb0df475098a0fb0675327cece6dd9c643a0c4d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147955"
---
# <a name="sccwillcreatesccfile-function"></a>Função SccWillCreateSccFile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa função determina se o plug-in de controle do código-fonte dá suporte à criação do MSSCCPRJ. Arquivo SCC para cada um dos arquivos fornecidos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 no O ponteiro de contexto do plug-in de controle do código-fonte.  
  
 nFiles  
 no O número de nomes de arquivo incluídos na `lpFileNames` matriz, bem como o comprimento da `pbSccFiles` matriz.  
  
 lpFileNames  
 no Uma matriz de nomes de arquivos totalmente qualificados a serem verificados (a matriz deve ser alocada pelo chamador).  
  
 pbSccFiles  
 [entrada, saída] Matriz na qual armazenar os resultados.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Sucesso.|  
|SCC_E_INVALIDFILEPATH|Um dos caminhos na matriz é inválido.|  
|SCC_E_NONSPECIFICERROR|Falha não específica.|  
  
## <a name="remarks"></a>Comentários  
 Essa função é chamada com uma lista de arquivos para determinar se o plug-in de controle do código-fonte fornece suporte no MSSCCPRJ. Arquivo SCC para cada um dos arquivos fornecidos (para obter mais informações sobre o MSSCCPRJ. Arquivo SCC, consulte [MSSCCPRJ. Arquivo SCC](../extensibility/mssccprj-scc-file.md)). Plug-ins de controle do código-fonte podem declarar se eles têm a capacidade de criar MSSCCPRJ. Arquivos SCC declarando `SCC_CAP_SCCFILE` durante a inicialização. O plug-in retorna `TRUE` ou `FALSE` por arquivo na `pbSccFiles` matriz para indicar quais dos arquivos determinados têm MSSCCPRJ. Suporte a SCC. Se o plug-in retornar um código de êxito da função, os valores na matriz de retorno serão respeitados. Em caso de falha, a matriz é ignorada.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções da API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)   
 [Arquivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
