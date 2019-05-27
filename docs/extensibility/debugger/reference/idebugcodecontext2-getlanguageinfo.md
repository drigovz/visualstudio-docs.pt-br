---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8e2ecbd9e33eaf43df9937eabd7d9149d3e85f4d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206735"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtém as informações de idioma para este contexto de código.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Parâmetros
`pbstrLanguage`\
[no, out] Retorna uma cadeia de caracteres que contém o nome da linguagem, como "C++."

`pguidLanguage`\
[no, out] Retorna o GUID para o idioma do contexto de código, por exemplo, `guidCPPLang`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Pelo menos um dos parâmetros deve retornar um valor não nulo.

## <a name="see-also"></a>Consulte também
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)