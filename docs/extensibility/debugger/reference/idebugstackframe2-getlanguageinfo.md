---
title: IDebugStackFrame2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5b6b5a94b38e1d057e51fe8f3ad8ed8e0003e4e
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203286"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo
Obtém o idioma associado a esse registro de ativação.

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
[out] Retorna o nome da linguagem que implementa o método associado deste quadro de pilhas.

`pguidLanguage`\
[out] Retorna o `GUID` da linguagem. Para o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] linguagens, por exemplo, o seguinte pode ser retornado:

-   `guidVBScriptLang`\

-   `guidJScriptLang`\

-   `guidCPPLang`\

-   `guidVBLang`\

-   `guidSQLLang`\

-   `guidScriptLang`\

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)