---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a8ca4ab504a9da2a63d5c70330d50e2c97e09817
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088225"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Adiciona uma instância filho do `IScriptEntry`.  
  
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
 [in] O índice do filho no pai.  
  
 `dwCookie`  
 [in] Um valor definido pelo aplicativo usado para associar a entrada de filho com o objeto de host.  
  
 `pszDelimiter`  
 [in] O endereço do delimitador de fim do bloco de script. Para analisar, o host normalmente usa um delimitador (como duas aspas simples), para detectar o final do bloco de script.  
  
 O delimitador permite que o script de criação de mecanismo para fornecer o pré-processamento. Por exemplo, o mecanismo pode substituir uma aspa simples por duas aspas simples para uso como um delimitador. O mecanismo determina como o delimitador é usado.  
  
 Definido como NULL se um delimitador não marca o final do bloco de script.  
  
 `ppse`  
 [out] O endereço de uma variável que recebe um ponteiro para o `IScriptEntry` interface da instância filho.  
  
 Para `IScriptNode` objetos que representam uma página da Web, este parâmetro retorna um `IScriptEntry` instância que especifica um bloco de script.  
  
 Para `IScriptEntry` objetos que representam um bloco de script, esse parâmetro retorna um `IScriptEntry` instância que especifica um objeto de função.  
  
 Para `IScriptEntry` objetos que representam uma função de objeto, esse método falhar.  
  
 Para `IScriptScriptlet` objetos, esse método falhar.  
  
## <a name="return-value"></a>Valor de retorno  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 O `IScriptNode` interface representa uma página da Web ou seus elementos. O `IScriptEntry` interface (que é derivado de `IScriptNode`) representa um bloco de script ou um objeto de função. O `IScriptScriptlet` interface (que é derivado de `IScriptEntry`) representa um manipulador de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)