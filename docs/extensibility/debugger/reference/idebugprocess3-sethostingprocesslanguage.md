---
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 170e5a2f315248164cf6af277197f7a9f9da05b5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933667"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
Esse método define o idioma que será hospedado no processo. Essa linguagem, em seguida, pode ser usada pelo mecanismo de depuração (DE) para carregar o avaliador de expressão apropriada.  
  
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
  
#### <a name="parameters"></a>Parâmetros  
 `guidLang`  
 [in] `GUID` da linguagem que o DE deve usar. Especificar `GUID_NULL` (C++) ou `Guid.Empty` (c#) para ter DE usar o idioma padrão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) pode ser usado para recuperar a configuração de idioma atual.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)