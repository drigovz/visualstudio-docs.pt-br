---
title: 'IDebugDocumentText:: gettext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e6472c40802fff4dad6e5ecc8f2729c95459e09f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572075"
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Recupera os caracteres e/ou os atributos de caractere associados a um intervalo de posição de caracteres.  
  
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
 no Local inicial do intervalo de posição de caracteres.  
  
 `pcharText`  
 [entrada, saída] Um buffer de texto de caractere. O buffer deve ser grande o suficiente para conter `cMaxChars` caracteres. Se esse parâmetro for nulo, o método não retornará caracteres.  
  
 `pstaTextAttr`  
 [entrada, saída] Um buffer de atributo de caractere. O buffer deve ser grande o suficiente para conter `cMaxChars` caracteres. Se esse parâmetro for nulo, o método não retornará atributos.  
  
 `pcNumChars`  
 [entrada, saída] O número de caracteres/atributos retornados. Esse parâmetro deve ser definido como zero antes de chamar este método.  
  
 `cMaxChars`  
 no Número de caracteres no intervalo de posição de caracteres. Também especifica o número máximo de caracteres a serem retornados.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método recupera os caracteres e/ou os atributos de caractere associados a um intervalo de posição de caracteres. O intervalo de posição de caracteres é especificado por uma posição de caracteres e um número de caracteres.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
 [SOURCE_TEXT_ATTR Enumeration](../../winscript/reference/source-text-attr-enumeration.md)