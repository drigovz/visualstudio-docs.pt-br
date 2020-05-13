---
title: IntelliSenseHostFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0df05e7363db01bd4f16fee5d75141dc93df1c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710264"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Especifica bandeiras de host do IntelliSense.

## <a name="syntax"></a>Sintaxe

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>parâmetros

|Membros|Descrição|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|O buffer de contexto é somente leitura.|
|`IHF_NOSEPARATESUBJECT`|Nenhum texto de assunto. O buffer de contexto contém o `!IHF_READONLYCONTEXT`alvo IntelliSense (implica ).|
|`IHF_SINGLELINESUBJECT`|O texto do assunto não é capaz de várias linhas.|
|`IHF_FORCECOMMITTOCONTEXT`|Igual a `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|A edição (em assunto ou contexto) deve ser feita no modo overtype.|

## <a name="requirements"></a>Requisitos
 SingleFileeditor.idl

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.TextManager.Interop>
