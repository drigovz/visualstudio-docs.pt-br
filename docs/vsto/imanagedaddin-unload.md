---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 296502aa461688c34152d86ee21aab5f2c83ecb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956738"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Chamado pouco antes um gerenciado suplemento VSTO é descarregado.

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valor retornado
 Um valor HRESULT que indica se o método concluída com êxito.

## <a name="remarks"></a>Comentários
 Esse método não é chamado por versões atuais do Microsoft Office. Este método está reservado para uso futuro.

## <a name="see-also"></a>Consulte também
- [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
