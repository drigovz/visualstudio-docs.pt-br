---
title: Enumerador de código de status de arquivo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711449"
---
# <a name="file-status-code-enumerator"></a>Enumerador de código de status de arquivo
O `SccStatus` enumerador contém valores constantes nomeados que especificam o estado de um arquivo no sistema de controle de origem. Esta enumeração é usada pelo [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e pela função de retorno de `POPLISTFUNC` chamada (consulte [POPLISTFUNC](../extensibility/poplistfunc.md) para obter detalhes).

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
 SCC_STATUS_INVALID status não pôde ser obtido; não confie nisso.

 SCC_STATUS_NOTCONTROLLED Arquivo não está sob controle de origem.

 SCC_STATUS_CONTROLLED Arquivo está sob controle de origem.

 SCC_STATUS_CHECKEDOUT Verificado pelo usuário atual no disco local.

 SCC_STATUS_OUTOTHER Arquivo é verificado por outro usuário.

 SCC_STATUS_OUTEXCLUSIVE Arquivo é exclusivamente verificado.

 SCC_STATUS_OUTMULTIPLE Arquivo é verificado por mais de um usuário.

 SCC_STATUS_OUTOFDATE O arquivo não é o mais recente.

 SCC_STATUS_DELETED Arquivo foi excluído do projeto.

 SCC_STATUS_LOCKED Arquivo está bloqueado; não são permitidas mais versões.

 SCC_STATUS_MERGED Arquivo foi mesclado, mas ainda não foi corrigido/verificado.

 SCC_STATUS_SHARED Arquivo é compartilhado entre projetos.

 SCC_STATUS_PINNED Arquivo é compartilhado com uma versão explícita.

 SCC_STATUS_MODIFIED Arquivo foi modificado/quebrado/violado.

 SCC_STATUS_OUTBYUSER Arquivo é verificado pelo usuário atual.

 SCC_STATUS_NOMERGE Arquivo nunca pode ser mesclado e não precisa ser salvo antes de um GET.

 SCC_STATUS_RESERVED_1 Reservado para uso interno.

 SCC_STATUS_RESERVED_2 Reservado para uso interno.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
