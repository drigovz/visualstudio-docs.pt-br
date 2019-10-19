---
title: 'IActiveScriptAuthor:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577252"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Adiciona o nome de um item de nível raiz ao namespace do mecanismo de criação de scripts. Um *item de nível raiz* é um objeto que pode conter Propriedades e métodos, e que também pode conter uma origem de evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszName`  
 no O nome do item como exibido no script. O nome deve ser exclusivo e persistente.  
  
 `dwFlags`  
 no Os sinalizadores associados ao item nomeado. Pode ser uma combinação dos seguintes valores:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Indica que o nome do item está disponível no namespace do script. Isso permite o acesso às propriedades, métodos e eventos do item.<br /><br /> Por convenção, as propriedades do item incluem os membros filho do item. Portanto, todas as propriedades e métodos do objeto filho (e seus membros filho, recursivamente) são acessíveis.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Indica os eventos da origem do item que o script pode ter manipuladores de eventos de script.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Indica que o item é uma coleção de propriedades globais e métodos que estão associados ao script. Seus membros são criados como variáveis e métodos globais.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Indica que o item deve ser salvo se o mecanismo de criação de scripts for salvo.|  
|SCRIPTITEM_CODEONLY|0x00000200|Indica que o item nomeado representa um objeto somente de código e não tem um membro para autor.|  
|SCRIPTITEM_NOCODE|0x00000400|Indica que o item nomeado é apenas um nome que está sendo adicionado e não tem nada a ser criado.|  
  
 `pdisp`  
 no O `IDispatch` do objeto `NamedItem` usado para coletar métodos, propriedades ou a origem do evento.  
  
## <a name="return-value"></a>Valor retornado  
 Um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)