---
title: 'IScriptNode:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573599"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Adiciona um Scriptlet como uma instância filho de um `IScriptNode`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszDefaultName`  
 no O endereço do nome padrão a ser associado ao scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Uma lista de identificadores do nome totalmente qualificado no host.  
  
 `cpszNames`  
 no O número de identificadores no parâmetro `prgpszNames`.  
  
 `pszEvent`  
 no O endereço de buffer que identifica o nome do evento associado ao scriptlet.  
  
 `pszDelimiter`  
 no O endereço do delimitador de bloco de fim do script. Para análise, o host normalmente usa um delimitador (como duas aspas simples) para detectar o final do bloco de script.  
  
 O delimitador habilita o pré-processamento pelo mecanismo de criação de scripts. Por exemplo, o mecanismo pode substituir uma aspa simples por duas aspas simples para uso como um delimitador. O mecanismo determina como o delimitador é usado.  
  
 Defina como NULL se nenhum delimitador for usado para identificar o final do bloco de script.  
  
 `ptiSignature`  
 no As informações de tipo para um objeto de função.  
  
 `iMethodSignature`  
 no O índice da função no parâmetro `ITypeInfo``ptiSignature`.  
  
 `isn`  
 no O índice do filho no pai.  
  
 `dwCookie`  
 no Um valor definido pelo aplicativo que é usado para associar a entrada ao objeto de host.  
  
 `ppse`  
 fora O endereço de uma variável que recebe um ponteiro para a interface de `IScriptEntry` da instância filho.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Um Scriptlet especifica um manipulador de eventos. Esse método cria um Scriptlet se for chamado por um objeto `IScriptNode` que representa uma página da Web. Esse método não terá sucesso se for chamado por outras interfaces.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IScriptNode](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry Interface](../../winscript/reference/iscriptentry-interface.md)