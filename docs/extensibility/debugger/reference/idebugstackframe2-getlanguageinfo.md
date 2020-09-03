---
title: 'IDebugStackFrame2:: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cefb4bdd9d0c85311c63e6a988956301a6c2cc14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719706"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Obtém o idioma associado a este quadro de pilhas.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parâmetros

`pbstrLanguage`\
fora Retorna o nome do idioma que implementa o método associado a esse quadro de pilhas.

`pguidLanguage`\
fora Retorna o `GUID` do idioma. Para os [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] idiomas, por exemplo, o seguinte pode ser retornado:

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Valor Retornado

 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
