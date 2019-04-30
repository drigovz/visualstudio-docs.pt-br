---
title: IActiveScriptParse32::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 782c1d7bd2dd4c0708418ffd3e69c339dd993fde
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954850"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analisa o scriptlet de código fornecido, adicionando declarações no namespace e avaliando o código conforme apropriado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|||  
|-|-|  
|`pstrCode`|[in] Endereço do texto de scriptlet para avaliar. A interpretação dessa cadeia de caracteres depende da linguagem de script.|  
|`pstrItemName`|[in] Endereço do nome do item que fornece o contexto no qual o scriptlet deve ser avaliada. Se esse parâmetro for NULL, o código é avaliado no contexto de global do mecanismo de script.|  
|`punkContext`|[in] Endereço do objeto de contexto. Esse objeto é reservado para uso em um ambiente de depuração, em que tal contexto pode ser fornecido pelo depurador para representar um contexto de tempo de execução ativo. Se esse parâmetro for NULL, o mecanismo usa `pstrItemName` para identificar o contexto.|  
|`pstrDelimiter`|[in] Endereço do delimitador final do scriptlet. Quando `pstrCode` é analisado de um fluxo de texto, o host normalmente usa um delimitador, como duas aspas ("), para detectar o final do scriptlet. Esse parâmetro especifica o delimitador que o host usou, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o script faz mecanismo usa essas informações depende o mecanismo de script. Definir esse parâmetro como `NULL` se o host não usou um delimitador para marcar o final do scriptlet.|  
|`dwSourceContextCookie`|[in] Cookie usado para fins de depuração.|  
|`ulStartingLineNumber`|[in] Valor com base em zero que especifica em qual linha a análise começará.|  
|`dwFlags`|[in] Sinalizadores associados com o scriptlet. Pode ser uma combinação desses valores:|  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Se a diferença entre uma expressão computacional e uma instrução for importante mas sintaticamente ambígua a linguagem de script, esse sinalizador Especifica que o scriptlet deve ser interpretado como uma expressão, em vez de uma instrução ou uma lista de instruções. Por padrão, as instruções são assumidas a menos que a opção correta pode ser determinada a partir da sintaxe do texto de scriptlet.|  
|SCRIPTTEXT_ISPERSISTENT|Indica que o código adicionado durante esta chamada deve ser salvo se o mecanismo de script é salvo (por exemplo, por meio de uma chamada para `IPersist*::Save`), ou se o mecanismo de script for redefinido por uma transição de volta ao estado inicializado.|  
|SCRIPTTEXT_ISVISIBLE|Indica que o texto do script deve ser visível (e, portanto, pode ser chamado por nome) como um método global no espaço para nome do script.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Endereço de um buffer que recebe os resultados do processamento de scriptlet, ou `NULL` se o chamador não espera resultados (ou seja, o valor de SCRIPTTEXT_ISEXPRESSION não está definido).|  
|`pexcepinfo`|[out] Endereço de uma estrutura que recebe informações de exceção. Essa estrutura é preenchida se `IActiveScriptParse::ParseScriptText` retorna DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`DISP_E_EXCEPTION`|Uma exceção durante o processamento do scriptlet. O `pexcepinfo` parâmetro contém informações sobre a exceção.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_NOTIMPL`|Não há suporte para o método. O mecanismo de script não oferece suporte a tempo de execução de avaliação de expressões ou instruções.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script está no estado não inicializado ou fechado, ou o sinalizador SCRIPTTEXT_ISEXPRESSION foi definido e o mecanismo de script está no estado inicializado).|  
|`OLESCRIPT_E_SYNTAX`|Ocorreu um erro de sintaxe não especificado no scriptlet.|  
  
## <a name="remarks"></a>Comentários  
 Se o mecanismo de script estiver no estado inicializado, nenhum código será realmente avaliado durante esta chamada; em vez disso, esse código é na fila e executado quando o mecanismo de script é uma transição em (ou por meio de) o estado iniciado. Como a execução não é permitida no estado inicializado, ele é um erro para chamar esse método com o sinalizador SCRIPTTEXT_ISEXPRESSION quando estiver no estado inicializado.  
  
 O scriptlet pode ser uma expressão, uma lista de instruções ou qualquer coisa permitida pela linguagem de script. Por exemplo, esse método é usado na avaliação do HTML \<SCRIPT > marca, que permite que as instruções sejam executadas como a página HTML sendo construída, em vez de apenas compilá-las no estado de script.  
  
 O código passado para esse método deve ser uma parte válida e completa do código. Por exemplo, no VBScript é ilegal chamar este método uma vez com Sub Function (x) e, em seguida, uma segunda vez com `End Sub`. O analisador não deve esperar a segunda chamada para concluir a sub-rotina, mas em vez disso, deve gerar um erro de análise porque uma declaração de sub-rotina foi iniciada, mas não concluída.  
  
 Para obter mais informações sobre estados de script, consulte a seção de estados de mecanismo de Script do [mecanismos de Script do Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)