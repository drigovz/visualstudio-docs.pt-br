---
title: IDebugPortPicker::DisplayPortPicker | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3dd9317a73800a3886a5a807e9e28b0c24b2301c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188374"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Exibe a caixa de diálogo especificada que permite que o usuário seleciona uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```csharp  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `hwndParentDialog`  
 [in] Identificador para a caixa de diálogo pai.  
  
 `pbstrPortId`  
 [out] Cadeia de caracteres de identificador de porta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Um valor de retorno `S_FALSE` (ou um valor de retorno `S_OK` com o `BSTR` definido como `NULL`) indica que o usuário clicou **Cancelar**.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
