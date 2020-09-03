---
title: Enumerador de código de status de diretório | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185247"
---
# <a name="directory-status-code-enumerator"></a>Enumerador de código de status do diretório
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O `SccDirStatus` enumerador contém valores constantes nomeados que especificam o estado de um diretório no sistema de controle do código-fonte. Essa enumeração é usada pelo [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Isso foi introduzido na versão 1,2 da API de plug-in de controle do código-fonte.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Membros  
 SCC_DIRSTATUS_INVALID  
 Não foi possível obter o status; Não confie nela.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 O diretório não está no controle do código-fonte.  
  
 SCC_DIRSTATUS_CONTROLLED  
 O diretório está sob controle do código-fonte.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 O projeto correspondente a este diretório está vazio.  
  
## <a name="see-also"></a>Consulte Também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
