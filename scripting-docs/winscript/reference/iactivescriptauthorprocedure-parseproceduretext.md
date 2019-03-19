---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149374"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analisa um procedimento de código, adiciona o texto do procedimento de código para o mecanismo de criação de script e cria um `IScriptEntry` objeto que corresponde ao procedimento de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCode`  
 [in] O texto do script para analisar.  
  
 `pszFormalParams`  
 [in] O endereço dos nomes de parâmetro formal para o procedimento. Os nomes de parâmetro devem ser separados pelos delimitadores apropriados para o mecanismo de criação de script. Os nomes não deverão ser incluídos em parênteses.  
  
 `pszProcedureName`  
 [in] O endereço do nome do procedimento a ser analisado.  
  
 `pszItemName`  
 [in] O endereço do buffer que contém o nome do item associado com o `IScriptEntry` objeto.  
  
 `pszDelimiter`  
 [in] O endereço do delimitador de fim do bloco de script. Quando `pszCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador (como duas aspas simples), para detectar o fim do bloco de script. Defina esse parâmetro como NULL se não houver nenhum delimitador para marcar o fim do bloco de script.  
  
 `dwCookie`  
 [in] Um valor definido pelo aplicativo que está associado com o novo `IScriptEntry` objeto.  
  
 `dwFlags`  
 [in] Não usado.  
  
 `pdispFor`  
 [in] Não usado.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Atual [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] mecanismo não implementa esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthorProcedure Interface](../../winscript/reference/iactivescriptauthorprocedure-interface.md)