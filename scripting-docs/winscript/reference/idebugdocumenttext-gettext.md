---
title: IDebugDocumentText::GetText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77cc255bcd04754cbfde4638b67a85f6fdc0a922
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091982"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera os caracteres de e/ou os atributos de caracteres associados com um intervalo de posição do caractere.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cCharacterPosition`  
 [in] Local do intervalo de posição do caractere inicial.  
  
 `pcharText`  
 [no, out] Um buffer de caracteres de texto. O buffer deve ser grande o suficiente para manter `cMaxChars` caracteres. Se esse parâmetro for NULL, o método não retorna caracteres.  
  
 `pstaTextAttr`  
 [no, out] Um buffer de atributo de caracteres. O buffer deve ser grande o suficiente para manter `cMaxChars` caracteres. Se esse parâmetro for NULL, o método não retorna atributos.  
  
 `pcNumChars`  
 [no, out] O número de caracteres/atributos retornados. Esse parâmetro deve ser definido como zero antes de chamar esse método.  
  
 `cMaxChars`  
 [in] Número de caracteres no intervalo de posição de caractere. Também especifica o número máximo de caracteres a serem retornados.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera os caracteres de e/ou os atributos de caracteres associados com um intervalo de posição do caractere. O intervalo de posição de caractere é especificado por uma posição de caractere e um número de caracteres.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)