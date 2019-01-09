---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec100214a43be6e1faf5e229ce6452432065002b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093386"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analisa o procedimento de código fornecido e adiciona um procedimento de anônimo para o espaço para nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrCode`  
 [in] O texto do procedimento para avaliar. A interpretação dessa cadeia de caracteres depende da linguagem de script.  
  
 `pstrFormalParams`  
 [in] Nomes de parâmetro formal para o procedimento. Os nomes de parâmetro devem ser separados com os delimitadores apropriados para o mecanismo de script. Os nomes não devem estar entre parênteses.  
  
 `pstrItemName`  
 [in] O nome do item nomeado que fornece o contexto no qual o procedimento deve ser avaliado. Se esse parâmetro for `NULL`, o código será avaliado no contexto de global do mecanismo de script.  
  
 `punkContext`  
 [in] O objeto de contexto. Esse objeto é reservado para uso em um ambiente de depuração, em que tal contexto pode ser fornecido pelo depurador para representar um contexto de tempo de execução ativo. Se esse parâmetro for `NULL`, o mecanismo usa `pstrItemName` para identificar o contexto.  
  
 `pstrDelimiter`  
 [in] O delimitador final do procedimento. Quando `pstrCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador, como duas aspas ("), para detectar o fim do procedimento. Esse parâmetro especifica o delimitador que o host usou, permitindo que o mecanismo de script fornecer algumas condicional, o pré-processamento primitivo (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações dependem o mecanismo de script. Definir esse parâmetro como `NULL` se o host não usou um delimitador para marcar o final do procedimento.  
  
 `dwSourceContextCookie`  
 [in] Valor definido pelo aplicativo que é usado para fins de depuração.  
  
 `ulStartingLineNumber`  
 [in] Valor de base zero que especifica a linha em que a análise começará.  
  
 `dwFlags`  
 [in] Sinalizadores associados com o procedimento. Pode ser uma combinação desses valores.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica que o código em `pstrCode` é uma expressão que representa o valor retornado do procedimento.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica que o `this` ponteiro está incluído no escopo do procedimento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica que os pais do `this` ponteiro são incluídos no escopo do procedimento.|  
  
 `ppdisp`  
 [out] Retorna um wrapper de expedição em que o método padrão é o procedimento analisado por este método.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_NOTIMPL`|Não há suporte para o método. O mecanismo de script não oferece suporte a adição de tempo de execução de procedimentos para o espaço para nome.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script está no estado não inicializado ou fechado).|  
|`OLESCRIPT_E_SYNTAX`|Ocorreu um erro de sintaxe não especificado no procedimento.|  
|`S_FALSE`|O mecanismo de script não dá suporte a um objeto de expedição; o `ppdisp`parâmetro é definido como `NULL`.|  
  
## <a name="remarks"></a>Comentários  
 Nenhum código de script é avaliado durante esta chamada; em vez disso, o procedimento é compilado em um método no `ppdisp` onde ele pode ser chamado pelo script mais tarde.  
  
 Essa interface é preterida em favor do `IActiveScriptParseProcedure` interface. O `IActiveScriptParseProcedure::ParseProcedureText` método é semelhante a este método, mas permite que o nome do procedimento seja especificado. Em todas as circunstâncias, `IActiveScriptParseProcedure::ParseProcedureText` deve ser usado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)