---
title: Função SccEnumChangedFiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200127"
---
# <a name="sccenumchangedfiles-function"></a>Função SccEnumChangedFiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dada uma lista de arquivos locais, essa função determina quais arquivos são diferentes das versões correspondentes no banco de dados de controle do código-fonte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 pContext  
 no O ponteiro de contexto do plug-in de controle do código-fonte.  
  
 hWnd  
 no Um identificador para a janela do IDE que o plug-in de controle do código-fonte pode usar como um pai para qualquer caixa de diálogo que ele fornecer.  
  
 recfiles  
 no Número de nomes de arquivo especificados na `lpFileNames` matriz. Também especifica o tamanho da `plIsFileDifferent` matriz.  
  
 lpFileNames  
 no Matriz de nomes de arquivos locais a serem verificados.  
  
 plIsFileDifferent  
 [entrada, saída] Matriz de valores que indica o status de diferença de cada arquivo (a matriz deve ter pelo menos `cFiles` entradas). Zero significa que o arquivo é diferente.  
  
## <a name="return-value"></a>Valor Retornado  
 Espera-se que a implementação de plug-in de controle do código-fonte dessa função retorne um dos seguintes valores:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Operação concluída com sucesso.|  
|SCC_UNSPECIFIEDERROR|Erro genérico.|  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de API de plug-in de controle do código-fonte](../extensibility/source-control-plug-in-api-functions.md)
