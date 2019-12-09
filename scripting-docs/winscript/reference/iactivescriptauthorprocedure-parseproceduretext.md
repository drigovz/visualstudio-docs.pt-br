---
title: IActiveScriptAuthorProcedure::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572824"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Analisa um procedimento de código, adiciona o texto do procedimento de código ao mecanismo de criação de script e cria um objeto `IScriptEntry` que corresponde ao procedimento de código.  
  
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
 no O texto do script a ser analisado.  
  
 `pszFormalParams`  
 no O endereço dos nomes de parâmetro formais para o procedimento. Os nomes de parâmetro devem ser separados pelos delimitadores apropriados para o mecanismo de criação de scripts. Os nomes não devem ser colocados entre parênteses.  
  
 `pszProcedureName`  
 no O endereço do nome do procedimento a ser analisado.  
  
 `pszItemName`  
 no O endereço de buffer que contém o nome do item associado ao objeto `IScriptEntry`.  
  
 `pszDelimiter`  
 no O endereço do delimitador de bloco de fim do script. Quando `pszCode` é analisada a partir de um fluxo de texto, o host normalmente usa um delimitador (como duas aspas simples) para detectar o final do bloco de script. Defina esse parâmetro como NULL se não houver nenhum delimitador para marcar o final do bloco de script.  
  
 `dwCookie`  
 no Um valor definido pelo aplicativo que está associado ao novo objeto `IScriptEntry`.  
  
 `dwFlags`  
 no Não usado.  
  
 `pdispFor`  
 no Não usado.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O mecanismo de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] atual não implementa esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptAuthorProcedure Interface](../../winscript/reference/iactivescriptauthorprocedure-interface.md)