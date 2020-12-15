---
title: IntelliSenseHostFlags | Microsoft Docs
description: A enumeração IntelliSenseHostFlags especifica sinalizadores de host IntelliSense. Este artigo descreve os valores de enumeração.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b206cc4aa7c1ff388d6868fa8a0533d15da094ff
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487498"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Especifica os sinalizadores de host IntelliSense.

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

### <a name="parameters"></a>Parâmetros

|Membros|Descrição|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|O buffer de contexto é somente leitura.|
|`IHF_NOSEPARATESUBJECT`|Nenhum texto de assunto. O buffer de contexto contém IntelliSense-Target (implica `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|O texto do assunto não é compatível com várias linhas.|
|`IHF_FORCECOMMITTOCONTEXT`|Mesmo que `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|A edição (no assunto ou no contexto) deve ser feita no modo sobrescrever.|

## <a name="requirements"></a>Requisitos
 SingleFileeditor. idl

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.TextManager.Interop>
