---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575757"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera a interface `IDispatch` para os métodos e propriedades associados ao script em execução no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrItemName`  
 no Endereço de um buffer que contém o nome do item para o qual o chamador precisa do objeto de expedição associado. Se esse parâmetro for `NULL`, o objeto de expedição conterá como seus membros todos os métodos globais e propriedades definidos pelo script. Por meio da interface de `IDispatch` e da interface `ITypeInfo` associada, o host pode invocar métodos de script ou exibir e modificar variáveis de script.  
  
 `ppdisp`  
 fora Endereço de uma variável que recebe um ponteiro para o objeto associado aos métodos e propriedades globais do script. Se o mecanismo de script não oferecer suporte a tal objeto, `NULL` será retornado.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
|`S_FALSE`|O mecanismo de script não dá suporte a um objeto de expedição; o parâmetro `ppdisp` é definido como NULL.|  
  
## <a name="remarks"></a>Comentários  
 Como os métodos e as propriedades podem ser adicionados chamando a interface [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , a interface `IDispatch` retornada por esse método pode dar suporte dinamicamente a novos métodos e propriedades. Da mesma forma, o método `IDispatch::GetTypeInfo` deve retornar uma interface de `ITypeInfo` nova e exclusiva quando métodos e propriedades forem adicionados. No entanto, observe que os mecanismos de linguagem não devem alterar a interface `IDispatch` de forma que seja incompatível com qualquer interface de `ITypeInfo` anterior retornada. Isso implica, por exemplo, que os DISPIDs nunca serão reutilizados.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)