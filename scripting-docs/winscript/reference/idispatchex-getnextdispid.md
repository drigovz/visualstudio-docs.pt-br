---
title: 'IDispatchEx:: GetNextDispID | Microsoft Docs'
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
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144423"
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

## <a name="parameters"></a>parâmetros

`grfdex`\
Determina qual conjunto de itens deve ser enumerado. Isso pode ser uma combinação dos seguintes valores:

|Valor|Significado|
|-----------|-------------|
|fdexEnumDefault|Solicita que o objeto enumere os elementos padrão. O objeto tem permissão para enumerar qualquer conjunto de elementos.|
|fdexEnumAll|Solicita que o objeto Enumere todos os elementos. O objeto tem permissão para enumerar qualquer conjunto de elementos.|

`id`\
Identifica o membro atual. GetNextDispID recupera o item na enumeração após este. Usa getdispid ou uma chamada anterior para GetNextDispID para obter esse identificador. Usa o valor DISPID_STARTENUM para obter o primeiro identificador do primeiro item.

`pid`\
Endereço de uma variável DISPID que recebe o identificador do próximo item na enumeração.

Se um membro for excluído pelo `DeleteMemberByName` ou `DeleteMemberByDispID` , o `DISPID` precisa permanecer válido para `GetNextDispID` .

## <a name="return-value"></a>Valor retornado

Retorna um dos seguintes valores:

|Valor|Significado|
|-|-|
|`S_OK`|Êxito.|
|`S_FALSE`|A enumeração é feita.|

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

## <a name="see-also"></a>Confira também

- [Interface IDispatchEx](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)