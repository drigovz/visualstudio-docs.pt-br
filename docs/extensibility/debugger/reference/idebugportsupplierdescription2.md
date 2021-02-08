---
title: IDebugPortSupplierDescription2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3db59d4938911d0c47f0122a8727be8f1c8acd67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840191"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Permite que a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interface do usuário exiba texto dentro da seção **informações de transporte** da caixa de diálogo **anexar ao processo** .

## <a name="syntax"></a>Sintaxe

```
IDebugPortSupplierDescription2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por fornecedores de porta.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugPortSupplierDescription2` .

|Método|Descrição|
|------------|-----------------|
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera os metadados de descrição e descrição para o fornecedor da porta.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
