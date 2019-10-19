---
title: IDebugDocumentHelper::D efineScriptBlock | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576975"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica ao auxiliar que um intervalo específico de caracteres é um bloco de script que é manipulado pelo mecanismo de script fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ulCharOffset`  
 no Local do início do bloco de script.  
  
 `cChars`  
 no Número de caracteres no bloco de script.  
  
 `pas`  
 no O mecanismo de script para este bloco de script.  
  
 `fScriptlet`  
 no Sinalizador que indica se o bloco de script é um Scriptlet.  
  
 `pdwSourceContext`  
 fora O contexto de origem do bloco de script.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um host inteligente pode usar esse método quando seus documentos contiverem blocos de script inseridos. Um mecanismo de linguagem pode usar esse método quando seu código contém scripts inseridos para outros idiomas.  
  
 O mecanismo de script é responsável por todas as cores de sintaxe e as pesquisas de contexto de código no bloco de script.  
  
 O método `DefineScriptBlock` deve ser chamado depois que o texto tiver sido adicionado (por exemplo, usando o método `IDebugDocumentHelper::AddDBCSText`), mas antes de o bloco de script ter sido analisado (por exemplo, usando o método `IActiveScriptParse ::ParseScriptText`).  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)