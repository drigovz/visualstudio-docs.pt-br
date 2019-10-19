---
title: Enumeração SOURCE_TEXT_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572996"
---
# <a name="source_text_attr-enumeration"></a>Enumeração SOURCE_TEXT_ATTR
Descrevem os atributos de um único caractere de texto de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|O caractere é parte de uma palavra-chave de linguagem, por exemplo, a palavra-chave VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|O caractere é parte de um bloco de comentário.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|O caractere não faz parte do texto de origem da linguagem compilada. Por exemplo, o HTML em torno de um bloco de script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|O caractere é parte de um operador de linguagem. Por exemplo:, o operador aritmético **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|O caractere é parte de uma constante numérica de idioma.  Por exemplo, a constante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|O caractere é parte de uma constante de cadeia de caracteres de linguagem. Por exemplo, a cadeia de caracteres "Olá, Mundo".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|O caractere indica o início de um bloco de função|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, os métodos `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` e `IActiveScriptDebug::GetScriptTextAttributes` retornam um atributo de texto por caractere, a menos que:  
  
- O sinalizador GETATTRTYPE_DEPSCAN é definido; nesse caso, o método pode retornar os sinalizadores SOURCETEXT_ATTR_IDENTIFIER e SOURCETEXT_ATTR_MEMBERLOOKUP,  
  
- O sinalizador GETATTRFLAG_THIS é definido; nesse caso, o método pode retornar o sinalizador SOURCETEXT_ATTR_THIS,  
  
- O sinalizador GETATTRFLAG_HUMANTEXT é definido; nesse caso, o método pode retornar o sinalizador SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)