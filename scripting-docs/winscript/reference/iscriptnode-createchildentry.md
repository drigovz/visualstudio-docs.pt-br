---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573611"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Adiciona uma instância filho de `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `isn`  
 no O índice do filho no pai.  
  
 `dwCookie`  
 no Um valor definido pelo aplicativo usado para associar a entrada filho ao objeto de host.  
  
 `pszDelimiter`  
 no O endereço do delimitador de bloco de fim do script. Para análise, o host normalmente usa um delimitador (como duas aspas simples) para detectar o final do bloco de script.  
  
 O delimitador permite que o mecanismo de criação de scripts forneça pré-processamento. Por exemplo, o mecanismo pode substituir uma aspa simples por duas aspas simples para uso como um delimitador. O mecanismo determina como o delimitador é usado.  
  
 Defina como NULL se um delimitador não marcar o final do bloco de script.  
  
 `ppse`  
 fora O endereço de uma variável que recebe um ponteiro para a interface de `IScriptEntry` da instância filho.  
  
 Para `IScriptNode` objetos que representam uma página da Web, esse parâmetro retorna uma instância de `IScriptEntry` que especifica um bloco de script.  
  
 Para `IScriptEntry` objetos que representam um bloco de script, esse parâmetro retorna uma instância de `IScriptEntry` que especifica um objeto de função.  
  
 Para `IScriptEntry` objetos que representam um objeto de função, esse método falha.  
  
 Para objetos `IScriptScriptlet`, esse método falha.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 A interface `IScriptNode` representa uma página da Web ou seus elementos. A interface de `IScriptEntry` (que é derivada de `IScriptNode`) representa um bloco de script ou um objeto de função. A interface `IScriptScriptlet` (que é derivada de `IScriptEntry`) representa um manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)