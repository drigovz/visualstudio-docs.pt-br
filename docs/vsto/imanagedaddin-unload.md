---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a36599259a38d0b9b8eb814a457b3625d593b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934592"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Chamado pouco antes de um suplemento do VSTO gerenciado ser descarregado.

## <a name="syntax"></a>Sintaxe

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Valor retornado
 Um valor HRESULT que indica se o método foi concluído com êxito.

## <a name="remarks"></a>Comentários
 Esse método não é chamado pelas versões atuais do Microsoft Office. Este método está reservado para uso futuro.

## <a name="see-also"></a>Confira também
- [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
