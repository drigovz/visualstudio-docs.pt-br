---
title: IActiveScriptParse::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee5d76060789118e9051c2d8dcc5fc570617f6a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954944"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Adiciona um scriptlet de código ao script. Esse método é usado em ambientes onde o estado persistente do script está entremeado com o documento de host e o host é responsável por restaurar o script, em vez de por meio um `IPersist*` interface. Os exemplos primários são linguagens de script HTML que permitem miniscripts de código inserido no documento HTML a ser anexado a eventos intrínsecos (por exemplo, ONCLICK="button1.text='Exit'").  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrDefaultName`  
 [in] Endereço de um nome padrão para associar o scriptlet. Se o scriptlet não contiver informações de nomeação (como no exemplo ONCLICK acima), esse nome será usado para identificar o scriptlet. Se esse parâmetro for `NULL`, o mecanismo de script fabrica um nome exclusivo, se necessário.  
  
 `pstrCode`  
 [in] Endereço do texto de scriptlet a ser adicionado. A interpretação dessa cadeia de caracteres depende da linguagem de script.  
  
 `pstrItemName`  
 [in] Endereço de um buffer que contém o nome do item associado a este scriptlet. Esse parâmetro, além de `pstrSubItemName`, identifica o objeto para o qual o scriptlet é um manipulador de eventos.  
  
 `pstrSubItemName`  
 [in] Endereço de um buffer que contém o nome de um `subobject` do item nomeado com a qual este scriptlet está associado; esse nome deve ser encontrado nas informações de tipo do item nomeado. Esse parâmetro é NULL se o scriptlet deve ser associado ao item nomeado, em vez de um `subitem`. Esse parâmetro, além de `pstrItemName`, identifica o objeto específico para o qual o scriptlet é um manipulador de eventos.  
  
 `pstrEventName`  
 [in] Endereço de um buffer que contém o nome do evento para o qual o scriptlet é um manipulador de eventos.  
  
 `pstrDelimiter`  
 [in] Endereço do delimitador final do scriptlet. Quando o `pstrCode` parâmetro é analisado a partir de um fluxo de texto, o host normalmente usa um delimitador, como duas aspas ("), para detectar o final do scriptlet. Esse parâmetro especifica o delimitador que o host usou, permitindo que o mecanismo de script forneça algum pré-processamento primitivo condicional (por exemplo, substituindo uma aspa simples ['] por duas aspas simples para uso como um delimitador). Exatamente como (e se) o script faz mecanismo usa essas informações depende o mecanismo de script. Defina esse parâmetro como NULL se o host não usou um delimitador para marcar o final do scriptlet.  
  
 `dwSourceContextCookie`  
 [in] Valor definido pelo aplicativo que é usado para fins de depuração.  
  
 `ulStartingLineNumber`  
 [in] Valor com base em zero que especifica em qual linha a análise começará.  
  
 `dwFlags`  
 [in] Sinalizadores associados com o scriptlet. Pode ser uma combinação dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Indica que o texto do script deve ser visível (e, portanto, pode ser chamado por nome) como um método global no espaço para nome do script.|  
|SCRIPTTEXT_ISPERSISTENT|Indica que o código adicionado durante esta chamada deve ser salvo se o mecanismo de script é salvo (por exemplo, por meio de uma chamada para `IPersist*::Save`), ou se o mecanismo de script for redefinido por uma transição de volta ao estado inicializado. Para obter mais informações sobre esse estado, consulte estados de mecanismo de Script.|  
  
 `pbstrName` ,  
 [out] Nome real usado para identificar o scriptlet. Isso é para estar na ordem de preferência: um nome especificado explicitamente no texto de scriptlet, o nome padrão fornecido no `pstrDefaultName`, ou um nome exclusivo sintetizadas pelo mecanismo de script.  
  
 `pexcepinfo` ,  
 [out] Endereço de uma estrutura que contém informações de exceção. Essa estrutura deve ser preenchida se DISP_E_EXCEPTION for retornado.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`DISP_E_EXCEPTION`|Ocorreu uma exceção na análise do scriptlet. O `pexcepinfo` parâmetro contém informações sobre a exceção.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_NOTIMPL`|Não há suporte para esse método; o mecanismo de script não oferece suporte à inclusão de miniscripts recepção de evento.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado) e, portanto, com falha.|  
|`OLESCRIPT_E_INVALIDNAME`|O nome padrão fornecido é inválido nessa linguagem de script.|  
|`OLESCRIPT_E_SYNTAX`|Ocorreu um erro de sintaxe não especificado no scriptlet.|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)