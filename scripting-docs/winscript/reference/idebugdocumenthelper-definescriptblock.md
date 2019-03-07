---
title: 'Idebugdocumenthelper:: Definescriptblock | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0037df270bc95faaba4d2f04cce65902d08dc6e9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087991"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
Indica para o auxiliar que um determinado intervalo de caracteres é um bloco de script que é tratado pelo mecanismo de script fornecido.  
  
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
 [in] Local do início do bloco de script.  
  
 `cChars`  
 [in] Número de caracteres no bloco de script.  
  
 `pas`  
 [in] O mecanismo de script para este bloco de script.  
  
 `fScriptlet`  
 [in] Sinalizador que indica se o bloco de script é um scriptlet.  
  
 `pdwSourceContext`  
 [out] O contexto de origem para o bloco de script.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um host inteligente pode usar esse método quando seus documentos contêm blocos de script inseridos. Um mecanismo de linguagem pode usar esse método quando seu código contém scripts inseridos para outros idiomas.  
  
 O mecanismo de script é responsável por todas as sintaxe código e a colorização contexto pesquisas no bloco de script.  
  
 O `DefineScriptBlock` método deve ser chamado depois que o texto foi adicionado (por exemplo, usando o `IDebugDocumentHelper::AddDBCSText` método), mas antes do script de bloco foi analisado (por exemplo, usando o `IActiveScriptParse ::ParseScriptText` método).  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Idebugdocumenthelper:: Adddbcstext](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)