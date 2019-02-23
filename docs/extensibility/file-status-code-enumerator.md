---
title: Enumerador de código de Status do arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50312caddf0ce2b5c64d1ec83e1707e2e0ee086e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713471"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de status do arquivo
O `SccStatus` enumerador contém valores constantes nomeados que especificam o estado de um arquivo no sistema de controle de origem. Essa enumeração é usada pelo [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e o `POPLISTFUNC` função de retorno de chamada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).

## <a name="syntax"></a>Sintaxe

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
 Não foi possível obter o Status de SCC_STATUS_INVALID; Não confie nele.

 Arquivo SCC_STATUS_NOTCONTROLLED não está sob controle de origem.

 Arquivo SCC_STATUS_CONTROLLED está sob controle de origem.

 SCC_STATUS_CHECKEDOUT check-out pelo usuário atual no disco local.

 SCC_STATUS_OUTOTHER arquivo foi extraído por outro usuário.

 Arquivo SCC_STATUS_OUTEXCLUSIVE é check-out exclusivo.

 Arquivo SCC_STATUS_OUTMULTIPLE é extraído por mais de um usuário.

 SCC_STATUS_OUTOFDATE o arquivo não é mais recente.

 SCC_STATUS_DELETED arquivo foi excluído do projeto.

 SCC_STATUS_LOCKED arquivo está bloqueado; Não há versões mais permitidos.

 Arquivo SCC_STATUS_MERGED foi mesclado, mas ainda não foi corrigido/verificado.

 Arquivo SCC_STATUS_SHARED é compartilhado entre projetos.

 Arquivo de SCC_STATUS_PINNED é compartilhado para uma versão explícita.

 SCC_STATUS_MODIFIED arquivo foi modificado/dividida/violada.

 Arquivo SCC_STATUS_OUTBYUSER é extraído por usuário atual.

 Arquivo SCC_STATUS_NOMERGE nunca podem ser mesclado com e não precisa ser salvo antes de um GET.

 SCC_STATUS_RESERVED_1 reservado para uso interno.

 SCC_STATUS_RESERVED_2 reservado para uso interno.

## <a name="see-also"></a>Consulte também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)