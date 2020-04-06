---
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a16f2c39fa2d53ffc4d113666ef7630557e61861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723573"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Este método define a linguagem em que o processo será hospedado. Esta linguagem pode então ser usada pelo mecanismo de depuração (DE) para carregar o avaliador de expressão apropriado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>parâmetros
`guidLang`\
[em] `GUID` da linguagem que o DE deve usar. Especifique `GUID_NULL` (C++) ou `Guid.Empty` (C#) para que o DE use o idioma padrão.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) pode ser usado para recuperar a configuração atual do idioma.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
