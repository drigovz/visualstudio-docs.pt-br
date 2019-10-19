---
title: IActiveScriptParseProcedureOld::P arseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577445"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analisa o procedimento de código fornecido e adiciona um procedimento anônimo ao espaço de nome.  
  
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
 no O texto do procedimento a ser avaliado. A interpretação dessa cadeia de caracteres depende da linguagem de script.  
  
 `pstrFormalParams`  
 no Nomes de parâmetro formais para o procedimento. Os nomes de parâmetro devem ser separados com os delimitadores apropriados para o mecanismo de script. Os nomes não devem ser colocados entre parênteses.  
  
 `pstrItemName`  
 no O nome do item nomeado que fornece o contexto no qual o procedimento deve ser avaliado. Se esse parâmetro for `NULL`, o código será avaliado no contexto global do mecanismo de script.  
  
 `punkContext`  
 no O objeto de contexto. Esse objeto é reservado para uso em um ambiente de depuração, onde tal contexto pode ser fornecido pelo depurador para representar um contexto de tempo de execução ativo. Se esse parâmetro for `NULL`, o mecanismo usará `pstrItemName` para identificar o contexto.  
  
 `pstrDelimiter`  
 no O delimitador de fim de procedimento. Quando `pstrCode` é analisada a partir de um fluxo de texto, o host geralmente usa um delimitador, como duas aspas simples (' '), para detectar o final do procedimento. Esse parâmetro especifica o delimitador usado pelo host, permitindo que o mecanismo de script forneça algum pré-processamento condicional e primitivo (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o mecanismo de script usa essas informações depende do mecanismo de script. Defina esse parâmetro como `NULL` se o host não usou um delimitador para marcar o final do procedimento.  
  
 `dwSourceContextCookie`  
 no Valor definido pelo aplicativo que é usado para fins de depuração.  
  
 `ulStartingLineNumber`  
 no Valor de base zero que especifica em qual linha a análise será iniciada.  
  
 `dwFlags`  
 no Sinalizadores associados ao procedimento. Pode ser uma combinação desses valores.  
  
|Constante|Valor|Significado|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Indica que o código em `pstrCode` é uma expressão que representa o valor de retorno do procedimento.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Indica que o ponteiro de `this` está incluído no escopo do procedimento.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Indica que os pais do ponteiro de `this` estão incluídos no escopo do procedimento.|  
  
 `ppdisp`  
 fora Retorna um wrapper de expedição em que o método padrão é o procedimento analisado por esse método.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_NOTIMPL`|Não há suporte para o método. O mecanismo de script não dá suporte à adição de procedimentos de tempo de execução para o espaço de nome.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script está no estado não inicializado ou fechado).|  
|`OLESCRIPT_E_SYNTAX`|Ocorreu um erro de sintaxe não especificado no procedimento.|  
|`S_FALSE`|O mecanismo de script não dá suporte a um objeto de expedição; o `ppdisp`parameter é definido como `NULL`.|  
  
## <a name="remarks"></a>Comentários  
 Nenhum código de script é avaliado durante esta chamada; em vez disso, o procedimento é compilado em um método em `ppdisp` onde ele pode ser chamado pelo script posteriormente.  
  
 Essa interface foi preterida em favor da interface `IActiveScriptParseProcedure`. O método `IActiveScriptParseProcedure::ParseProcedureText` é semelhante a esse método, mas permite que o nome do procedimento seja especificado. Em todas as circunstâncias, `IActiveScriptParseProcedure::ParseProcedureText` deve ser usado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)  
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)