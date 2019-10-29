---
title: 'IActiveScriptAuthor:: GetInfoFromContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetInfoFromContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetInfoFromContext
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8b9ad4677d580d495c72866be57712476d6a9c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985318"
---
# <a name="iactivescriptauthorgetinfofromcontext"></a>IActiveScriptAuthor::GetInfoFromContext
Retorna informações de tipo e posições de ancoragem para um determinado caractere em um bloco de código. Isso fornece informações para IntelliSense de membro, listas globais e dicas de parâmetro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszCode`  
 no O endereço da cadeia de caracteres de bloco de código usada para gerar os resultados da informação.  
  
 `cchCode`  
 no O comprimento do bloco de código.  
  
 `ichCurrentPosition`  
 no A posição do caractere em relação ao início do bloco.  
  
 `dwListTypesRequested`  
 no Os tipos de lista solicitados. Pode ser uma combinação dos seguintes valores:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_NOLIST|0x0000|Nenhuma lista.|  
|SCRIPT_CMPL_MEMBERLIST|0x0001|Lista de membros.|  
|SCRIPT_CMPL_ENUMLIST|0x0002|Lista de enums.|  
|SCRIPT_CMPL_PARAMLIST|0x0004|Lista de parâmetros do método de chamada.|  
|SCRIPT_CMPL_GLOBALLIST|0x0008|Lista global.|  
  
 O tipo SCRIPT_CMPL_GLOBALLIST é tratado como um item de conclusão padrão que pode ser combinado usando o operador OR com outros itens de conclusão. O mecanismo de criação de scripts primeiro tenta popular informações de tipo para outros itens de lista de conclusão. Se isso falhar, o mecanismo populará para SCRIPT_CMPL_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 fora O tipo de lista fornecido.  
  
 `pichListAnchorPosition`  
 fora O índice inicial do contexto que contém a posição atual. O índice inicial é relativo ao início do bloco.  
  
 Isso é preenchido somente quando o `dwListTypesRequested` inclui SCRIPT_CMPL_MEMBERLIST, SCRIPT_CMPL_ENUMLIST ou SCRIPT_CMPL_GLOBALLIST. Para outros tipos de lista solicitados, o resultado é indefinido.  
  
 `pichFuncAnchorPosition`  
 fora O índice inicial da chamada de função que contém a posição atual. O índice inicial é relativo ao início do bloco.  
  
 Isso é preenchido somente quando o contexto que contém a posição atual é uma chamada de função e quando `dwListTypesRequested` inclui SCRIPT_CMPL_PARAMLIST. Caso contrário, o resultado será indefinido.  
  
 `pmemid`  
 fora A MEMBERid da função, conforme definido por um tipo no parâmetro `IProvideMultipleClassInfo``ppunk` out.  
  
 Isso é preenchido somente quando o `dwListTypesRequested` inclui SCRIPT_CMPL_PARAMLIST.  
  
 `piCurrentParameter`  
 fora O índice do parâmetro que contém a posição atual. Se a posição atual estiver no nome da função,-1 será retornado.  
  
 O valor `piCurrentParameter` é populado somente quando `dwListTypesRequested` inclui SCRIPT_CMPL_PARAMLIST.  
  
 `ppunk`  
 As informações de tipo, que são fornecidas na forma de um objeto de `IProvideMultipleClassInfo`.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
   de [interface IProvideMultipleClassInfo](/dotnet/api/microsoft.visualstudio.ole.interop.iprovidemultipleclassinfo)  
 [IActiveScriptAuthor Interface](../../winscript/reference/iactivescriptauthor-interface.md)