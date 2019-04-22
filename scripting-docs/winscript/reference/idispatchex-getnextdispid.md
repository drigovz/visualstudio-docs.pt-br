---
title: IDispatchEx::GetNextDispID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d964a8744f1f0a28704dd0a1d5e0fd2e67aab1c
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58897667"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Enumera os membros do objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parâmetros

`grfdex`\
Determina qual conjunto de itens a serem enumerados. Isso pode ser uma combinação dos seguintes valores:

|Valor|Significado|
|-----------|-------------|
|fdexEnumDefault|Solicita que o objeto enumera os elementos padrão. O objeto tem permissão para enumerar qualquer conjunto de elementos.|
|fdexEnumAll|Solicita que o objeto enumera todos os elementos. O objeto tem permissão para enumerar qualquer conjunto de elementos.|

`id`\
Identifica o membro atual. GetNextDispID recupera o item na enumeração depois deste. Usa GetDispID ou uma chamada anterior a GetNextDispID para obter esse identificador. Usa o valor DISPID_STARTENUM para obter o identificador do primeiro item da primeira.

`pid`\
Endereço de uma variável DISPID que recebe o identificador do próximo item na enumeração.

Se um membro for excluído pelo `DeleteMemberByName` ou `DeleteMemberByDispID`, o `DISPID` deve permanecer válida para `GetNextDispID`.

## <a name="return-value"></a>Valor de retorno

Retorna um dos seguintes valores:

|||
|-|-|
|`S_OK`|Êxito.|
|`S_FALSE`|Enumeração é feita.|

## <a name="example"></a>Exemplo

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Consulte também

- [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)