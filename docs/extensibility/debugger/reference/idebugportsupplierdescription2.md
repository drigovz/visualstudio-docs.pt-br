---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69853e34788a2f24afe183dfbb7070e48f14aa46
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724359"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Habilita [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] que a ui exiba o texto dentro da seção Informações de **transporte** da caixa de diálogo **Anexar ao processo.**

## <a name="syntax"></a>Sintaxe

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Esta interface é implementada por fornecedores portuários.

## <a name="methods"></a>Métodos
 A tabela a seguir `IDebugPortSupplierDescription2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera os metadados de descrição e descrição do fornecedor da porta.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
