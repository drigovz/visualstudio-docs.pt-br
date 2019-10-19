---
title: 'IDebugDocumentHelper:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577050"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Notifica o auxiliar de que o texto fornecido está disponível, mas não fornece os caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cChars`  
 no Número de caracteres (Unicode) a serem adicionados.  
  
 `dwTextStartCookie`  
 no Cookie definido pelo host que representa a posição inicial do texto.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_FAIL`|O método falhou.|  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que o host adie o fornecimento de caracteres a serem adicionados até que sejam necessários, permitindo ao auxiliar gerar notificações precisas e informações de tamanho. O parâmetro `dwTextStartCookie` é um cookie, definido pelo host, que representa a posição inicial do texto. As chamadas subsequentes para `IDebugDocumentText::GetText` devem fornecer esse cookie. Por exemplo, em um host que representa texto em DBCS, o cookie pode ser um deslocamento de byte.  
  
 Supõe-se que uma única chamada para `IDebugDocumentText::GetText` possa obter caracteres de várias chamadas para `AddDeferredText`. As classes auxiliares também podem solicitar o mesmo intervalo de caracteres adiados mais de uma vez.  
  
> [!NOTE]
> Chamadas para `AddDeferredText` não devem ser misturadas com chamadas para `AddUnicodeText` ou `AddDBCSText`. Se isso ocorrer, `E_FAIL` será retornado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)