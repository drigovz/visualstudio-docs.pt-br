---
title: IActiveScriptParseProcedure::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53ed29c3e283af0f923590851cf9bf0655f7ac08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561543"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
Analisa o procedimento de código fornecido e adiciona o procedimento ao espaço de nome.  
  
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
 no Endereço do texto do procedimento a ser avaliado. A interpretação dessa cadeia de caracteres depende da linguagem de script.  
  
 `pstrFormalParams`  
 no Endereço dos nomes de parâmetro formais para o procedimento. Os nomes de parâmetro devem ser separados com os delimitadores apropriados para o mecanismo de script. Os nomes não devem ser colocados entre parênteses.  
  
 `pstrProcedureName`  
 no Endereço do nome do procedimento a ser analisado.  
  
 `pstrItemName`  
 no Endereço do nome do item que fornece o contexto no qual o procedimento deve ser avaliado. Se esse parâmetro for `NULL`, o código será avaliado no contexto global do mecanismo de script.  
  
 `punkContext`  
 no Endereço do objeto de contexto. Esse objeto é reservado para uso em um ambiente de depuração, onde tal contexto pode ser fornecido pelo depurador para representar um contexto de tempo de execução ativo. Se esse parâmetro for `NULL`, o mecanismo usará `pstrItemName` para identificar o contexto.  
  
 `pstrDelimiter`  
 no Endereço do delimitador de fim de procedimento. Quando `pstrCode` é analisada a partir de um fluxo de texto, o host geralmente usa um delimitador, como duas aspas simples (' '), para detectar o final do procedimento. Esse parâmetro especifica o delimitador usado pelo host, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações depende do mecanismo de script. Defina esse parâmetro como `NULL` se o host não usou um delimitador para marcar o final do procedimento.  
  
 `dwSourceContextCookie`  
 no Valor definido pelo aplicativo que é usado para fins de depuração.  
  
 `ulStartingLineNumber`  
 no Valor de base zero que especifica em qual linha a análise será iniciada.  
  
 `dwFlags`  
 no Sinalizadores associados ao procedimento. Pode ser uma combinação desses valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Indica que o código em `pstrCode` é uma expressão que representa o valor de retorno do procedimento. Por padrão, o código pode conter uma expressão, uma lista de instruções ou qualquer outra coisa permitida em um procedimento pela linguagem de script.|  
|SCRIPTPROC_IMPLICIT_THIS|Indica que o ponteiro de `this` está incluído no escopo do procedimento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Indica que os pais do ponteiro de `this` estão incluídos no escopo do procedimento.|  
  
 `ppdisp`  
 fora Endereço do ponteiro para o objeto que contém os métodos e as propriedades globais do script. Se o mecanismo de script não oferecer suporte a tal objeto, `NULL` será retornado.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_NOTIMPL`|Não há suporte para o método. O mecanismo de script não dá suporte à adição de procedimentos de tempo de execução para o espaço de nome.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script está no estado não inicializado ou fechado).|  
|`OLESCRIPT_E_SYNTAX`|Ocorreu um erro de sintaxe não especificado no procedimento.|  
|`S_FALSE`|O mecanismo de script não dá suporte a um objeto de expedição; o parâmetro `ppdisp` é definido como `NULL`.|  
  
## <a name="remarks"></a>Comentários  
 Nenhum código de script é avaliado durante esta chamada; em vez disso, o procedimento é compilado no estado do script, no qual ele pode ser chamado pelo script posteriormente.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)