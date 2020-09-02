---
title: Enumerador de código de status de arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204371"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de status do arquivo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O `SccStatus` enumerador contém valores constantes nomeados que especificam o estado de um arquivo no sistema de controle do código-fonte. Essa enumeração é usada pelo [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e pela `POPLISTFUNC` função de retorno de chamada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Membros  
 SCC_STATUS_INVALID  
 Não foi possível obter o status; Não confie nela.  
  
 SCC_STATUS_NOTCONTROLLED  
 O arquivo não está no controle do código-fonte.  
  
 SCC_STATUS_CONTROLLED  
 O arquivo está sob controle do código-fonte.  
  
 SCC_STATUS_CHECKEDOUT  
 Check-out feito pelo usuário atual no disco local.  
  
 SCC_STATUS_OUTOTHER  
 O check-out do arquivo foi feito por outro usuário.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 O check-out exclusivo do arquivo foi feito.  
  
 SCC_STATUS_OUTMULTIPLE  
 O check-out do arquivo foi feito por mais de um usuário.  
  
 SCC_STATUS_OUTOFDATE  
 O arquivo não é o mais recente.  
  
 SCC_STATUS_DELETED  
 O arquivo foi excluído do projeto.  
  
 SCC_STATUS_LOCKED  
 O arquivo está bloqueado; Não há mais nenhuma versão permitida.  
  
 SCC_STATUS_MERGED  
 O arquivo foi mesclado, mas ainda não foi corrigido/verificado.  
  
 SCC_STATUS_SHARED  
 O arquivo é compartilhado entre projetos.  
  
 SCC_STATUS_PINNED  
 O arquivo é compartilhado para uma versão explícita.  
  
 SCC_STATUS_MODIFIED  
 O arquivo foi modificado/interrompido/violado.  
  
 SCC_STATUS_OUTBYUSER  
 O check-out do arquivo foi feito pelo usuário atual.  
  
 SCC_STATUS_NOMERGE  
 O arquivo nunca pode ser mesclado com e não precisa ser salvo antes de um GET.  
  
 SCC_STATUS_RESERVED_1  
 Reservado para uso interno.  
  
 SCC_STATUS_RESERVED_2  
 Reservado para uso interno.  
  
## <a name="see-also"></a>Consulte Também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
