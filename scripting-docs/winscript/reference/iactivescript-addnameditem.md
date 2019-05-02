---
title: IActiveScript::AddNamedItem | Microsoft Docs
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
ms.openlocfilehash: db0a97c01d948a0c26850ebd1c3f47c6e3900614
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935791"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Adiciona o nome de um item de nível raiz para o espaço para nome do mecanismo de script. Um item de nível raiz é um objeto com propriedades e métodos, uma origem do evento ou todos os três.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pstrName`  
 [in] Endereço de um buffer que contém o nome do item, conforme exibido a partir do script. O nome deve ser exclusiva e persistente.  
  
 `dwFlags`  
 [in] Sinalizadores associados a um item. Pode ser uma combinação desses valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica que o item nomeado representa um objeto somente código, e que o host não tem nenhum `IUnknown` a ser associado este objeto somente código. O host tem apenas um nome para este objeto. Em linguagens orientadas a objeto, como o C++, esse sinalizador pode criar uma classe. Nem todas as linguagens dão suporte a esse sinalizador.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica que o item é uma coleção de propriedades globais e os métodos associados com o script. Normalmente, um mecanismo de script ignorará o nome do objeto (em vez de com a finalidade de usá-lo como um cookie para o [iactivescriptsite:: getItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) método, ou para a resolução de escopo explícito) e expor seus membros como global variáveis e métodos. Isso permite que o host estender a biblioteca (funções de tempo de execução e assim por diante) disponível para o script. Ele é deixado para o mecanismo de script para lidar com o nome entra em conflito (por exemplo, quando dois itens SCRIPTITEM_GLOBALMEMBERS têm métodos de mesmo nome), embora não deve ser retornado um erro devido a essa situação.|  
|SCRIPTITEM_ISPERSISTENT|Indica que o item deve ser salvo se o mecanismo de script é salvo. Da mesma forma, definir esse sinalizador indica que uma transição de volta ao estado inicializado deve reter informações nome e o tipo do item (o mecanismo de script no entanto, deve, liberar todos os ponteiros para interfaces no objeto real).|  
|SCRIPTITEM_ISSOURCE|Indica que o item de fontes de eventos que o script pode coletar. Objetos filho (Propriedades do objeto que são eles próprios objetos) também podem obter eventos para o script. Isso não é recursiva, mas ele fornece um mecanismo conveniente para o caso comum, por exemplo, de criar controles de um contêiner e todos os seus membros.|  
|SCRIPTITEM_ISVISIBLE|Indica que o nome do item está disponível no espaço para nome do script, permitindo o acesso para as propriedades, métodos e eventos do item. Por convenção, as propriedades do item incluem filhos do item; Portanto, todas as propriedades do objeto filho e métodos (e seus filhos, recursivamente) poderão ser acessados.|  
|SCRIPTITEM_NOCODE|Indica que o item é simplesmente um nome que está sendo adicionado ao espaço para nome do script e não deve ser tratado como um item para o qual código deve ser associado. Por exemplo, sem esse sinalizador definido, VBScript criará um módulo separado para o item nomeado e C++ pode criar uma classe wrapper separado para o item nomeado.|  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um dos seguintes valores:  
  
|Valor de retorno|Significado|  
|------------------|-------------|  
|`S_OK`|Êxito.|  
|`E_INVALIDARG`|Um argumento era inválido.|  
|`E_POINTER`|Um ponteiro inválido foi especificado.|  
|`E_UNEXPECTED`|A chamada não era esperada (por exemplo, o mecanismo de script ainda não foi carregado ou inicializado).|  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScript](../../winscript/reference/iactivescript.md)