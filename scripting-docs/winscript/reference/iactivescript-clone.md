---
title: 'IActiveScript:: clone | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575792"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona o mecanismo de script atual (menos qualquer estado de execução atual), retornando um mecanismo de script carregado que não tem nenhum site no thread atual. As propriedades desse novo mecanismo de script serão idênticas às propriedades em que o mecanismo de script original estaria se fosse transferido de volta para o estado inicializado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppscript`  
 fora Endereço de uma variável que recebe um ponteiro para a interface [IActiveScript](../../winscript/reference/iactivescript.md) do mecanismo de script clonado. O host deve criar um site e chamar o método [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) no novo mecanismo de script antes que ele esteja no estado Initialized e, portanto, pode ser usado.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_NOTIMPL`|Não há suporte para o método.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="remarks"></a>Comentários  
 O método `IActiveScript::Clone` é uma otimização de `IPersist*::Save`, `CoCreateInstance` e `IPersist*::Load`, de modo que o estado do novo mecanismo de script deve ser o mesmo que o estado do mecanismo de script original ter sido salvo e carregado em um novo mecanismo de script. Os itens nomeados são duplicados no mecanismo de script clonado, mas ponteiros de objeto específicos para cada item são esquecidos e obtidos com o método [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . Isso permite que um modelo de objeto idêntico com pontos de entrada por thread (um modelo de apartamento) seja usado.  
  
 Esse método é usado para hosts de servidor multithread que podem executar várias instâncias do mesmo script. O mecanismo de script pode retornar `E_NOTIMPL`; nesse caso, o host pode obter o mesmo resultado duplicando o estado persistente e criando uma nova instância do mecanismo de script com uma interface `IPersist*`.  
  
 Esse método pode ser chamado de threads não base sem resultar em um texto explicativo não base para hospedar objetos ou para a interface [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)