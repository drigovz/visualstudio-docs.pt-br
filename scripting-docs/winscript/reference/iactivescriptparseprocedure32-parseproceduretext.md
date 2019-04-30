---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993391"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analisa o procedimento de código fornecido e adiciona o procedimento para o espaço para nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrCode`  
 [in] Endereço do texto para avaliar o procedimento. A interpretação dessa cadeia de caracteres depende da linguagem de script.  
  
 `pstrFormalParams`  
 [in] Endereço de nomes de parâmetro formal para o procedimento. Os nomes de parâmetro devem ser separados com os delimitadores apropriados para o mecanismo de script. Os nomes não devem estar entre parênteses.  
  
 `pstrProcedureName`  
 [in] Endereço do nome do procedimento a ser analisado.  
  
 `pstrItemName`  
 [in] Endereço do nome do item que fornece o contexto no qual o procedimento deve ser avaliado. Se esse parâmetro for `NULL`, o código será avaliado no contexto de global do mecanismo de script.  
  
 `punkContext`  
 [in] Endereço do objeto de contexto. Esse objeto é reservado para uso em um ambiente de depuração, em que tal contexto pode ser fornecido pelo depurador para representar um contexto de tempo de execução ativo. Se esse parâmetro for `NULL`, o mecanismo usa `pstrItemName` para identificar o contexto.  
  
 `pstrDelimiter`  
 [in] Endereço do delimitador final do procedimento. Quando `pstrCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador, como duas aspas ("), para detectar o fim do procedimento. Esse parâmetro especifica o delimitador que o host usou, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o script faz mecanismo usa essas informações depende o mecanismo de script. Definir esse parâmetro como `NULL` se o host não usou um delimitador para marcar o final do procedimento.  
  
 `dwSourceContextCookie`  
 [in] Valor definido pelo aplicativo que é usado para fins de depuração.  
  
 `ulStartingLineNumber`  
 [in] Valor com base em zero que especifica em qual linha a análise começará.  
  
 `dwFlags`  
 [in] Sinalizadores associados com o procedimento. Pode ser uma combinação desses valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica que o código em `pstrCode` é uma expressão que representa o valor retornado do procedimento. Por padrão, o código pode conter uma expressão, uma lista de instruções ou qualquer coisa permitida ou em um procedimento de linguagem de script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica que o `this` ponteiro está incluído no escopo do procedimento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica que os pais do `this` ponteiro são incluídos no escopo do procedimento.|  
  
 `ppdisp`  
 [out] Endereço do ponteiro para o objeto que contém os métodos globais e as propriedades do script. Se o mecanismo de script não dá suporte a esse objeto, `NULL` será retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_NOTIMPL`|Não há suporte para o método. O mecanismo de script não oferece suporte a adição de tempo de execução de procedimentos para o espaço para nome.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script está no estado não inicializado ou fechado).|  
|`OLESCRIPT_E_SYNTAX`|Ocorreu um erro de sintaxe não especificado no procedimento.|  
|`S_FALSE`|O mecanismo de script não dá suporte a um objeto de expedição; o `ppdisp` parâmetro é definido como `NULL`.|  
  
## <a name="remarks"></a>Comentários  
 Nenhum código de script é avaliado durante esta chamada; em vez disso, o procedimento é compilado para o estado de script em que ele pode ser chamado pelo script mais tarde.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)