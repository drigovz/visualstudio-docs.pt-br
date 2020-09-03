---
title: POPDIRLISTFUNC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194057"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa é uma função de retorno de chamada fornecida para a função [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) para atualizar uma coleção de diretórios e (opcionalmente) nomes de arquivos para descobrir quais estão sob controle do código-fonte.  
  
 O `POPDIRLISTFUNC` retorno de chamada deve ser chamado somente para os diretórios e nomes de arquivo (na lista fornecida para a `SccPopulateDirList` função) que estão na verdade no controle do código-fonte.  
  
## <a name="signature"></a>Assinatura  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 pvCallerData  
 no Valor de usuário fornecido a [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [in] `TRUE` Se o nome no `lpDirectoryOrFileName` for um diretório; caso contrário, o nome será um nome de arquivo.  
  
 lpDirectoryOrFileName  
 no Caminho local completo para um diretório ou nome de arquivo que está sob controle do código-fonte.  
  
## <a name="return-value"></a>Valor Retornado  
 O IDE retorna um código de erro apropriado:  
  
|Valor|Descrição|  
|-----------|-----------------|  
|SCC_OK|Continuar o processamento.|  
|SCC_I_OPERATIONCANCELED|Pare o processamento.|  
|SCC_E_xxx|Qualquer erro de controle do código-fonte apropriado deve parar de processar.|  
  
## <a name="remarks"></a>Comentários  
 Se o `fOptions` parâmetro da `SccPopulateDirList` função contiver o `SCC_PDL_INCLUDEFILES` sinalizador, a lista provavelmente conterá nomes de arquivo, bem como nomes de diretório.  
  
## <a name="see-also"></a>Consulte Também  
 [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Códigos de Erro](../extensibility/error-codes.md)
