---
title: 'IActiveScript:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575821"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Adiciona o nome de um item de nível raiz ao espaço de nome do mecanismo de script. Um item de nível raiz é um objeto com propriedades e métodos, uma fonte de eventos ou todos os três.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrName`  
 no Endereço de um buffer que contém o nome do item como exibido no script. O nome deve ser exclusivo e persistente.  
  
 `dwFlags`  
 no Sinalizadores associados a um item. Pode ser uma combinação desses valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica que o item nomeado representa um objeto somente de código e que o host não tem `IUnknown` ser associado a esse objeto somente de código. O host tem apenas um nome para esse objeto. Em linguagens orientadas a objeto C++, como, esse sinalizador criaria uma classe. Nem todos os idiomas dão suporte a esse sinalizador.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica que o item é uma coleção de propriedades globais e métodos associados ao script. Normalmente, um mecanismo de script ignoraria o nome do objeto (exceto pelo propósito de usá-lo como um cookie para o método [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) ou para resolver o escopo explícito) e expor seus membros como variáveis e métodos globais. Isso permite que o host estenda a biblioteca (funções de tempo de execução e assim por diante) disponíveis para o script. Ele é deixado para o mecanismo de script para lidar com conflitos de nome (por exemplo, quando dois itens de SCRIPTITEM_GLOBALMEMBERS têm métodos de mesmo nome), embora não seja possível retornar um erro devido a essa situação.|  
|SCRIPTITEM_ISPERSISTENT|Indica que o item deve ser salvo se o mecanismo de script for salvo. Da mesma forma, definir esse sinalizador indica que uma transição de volta para o estado inicializado deve manter as informações de nome e tipo do item (o mecanismo de script deve, no entanto, liberar todos os ponteiros para interfaces no objeto real).|  
|SCRIPTITEM_ISSOURCE|Indica que o item origina os eventos que o script pode coletar. Objetos filho (Propriedades do objeto que estão em objetos próprios) também podem gerar eventos de origem para o script. Isso não é recursivo, mas fornece um mecanismo conveniente para o caso comum, por exemplo, da criação de um contêiner e de todos os seus controles de membros.|  
|SCRIPTITEM_ISVISIBLE|Indica que o nome do item está disponível no espaço de nome do script, permitindo o acesso às propriedades, aos métodos e aos eventos do item. Por convenção, as propriedades do item incluem os filhos do item; Portanto, todas as propriedades e métodos do objeto filho (e seus filhos, recursivamente) estarão acessíveis.|  
|SCRIPTITEM_NOCODE|Indica que o item é simplesmente um nome que está sendo adicionado ao espaço de nome do script e não deve ser tratado como um item para o qual o código deve ser associado. Por exemplo, sem esse sinalizador ser definido, o VBScript criará um módulo separado para o item nomeado e C++ poderá criar uma classe wrapper separada para o item nomeado.|  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um dos seguintes valores:  
  
|Valor retornado|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)