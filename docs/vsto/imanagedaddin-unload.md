---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4aa3c07ed715a6118bd053d44503607a889f3da7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880882"
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
 [Interface IManagedAddin](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Load](../vsto/imanagedaddin-load.md)  
