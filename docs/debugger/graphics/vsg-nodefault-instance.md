---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675bd0ceef2b8eef382891bf0fc4b42400ca9df4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018651"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Define por sua presença se uma instância padrão do [classe VsgDbg](vsgdbg-class.md) classe — que fornece a interface de captura programática — é fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Valor  
 Um pré-processador de símbolo que por sua presença ou ausência determina se uma instância padrão do `VsgDbg` classe é fornecida. Se esse símbolo é definido, em seguida, nenhuma instância padrão do `VsgDbg` classe é fornecida; caso contrário, uma instância padrão é fornecida e inicializada antes que o programa é executado.  
  
 A interface de captura programática é fornecido por meio de um ponteiro que tem escopo global, `g_pVsgDbg`.  
  
```cpp
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Comentários  
 A instância padrão geralmente é suficiente, mas para usar a interface de captura programática dentro de uma DLL, quando o dispositivo D3D foi criado fora dessa DLL, você deve criar e gerenciar sua própria instância da `VsgDbg` classe. Se você estiver gerenciando sua própria interface para a API de captura programática dessa maneira, desabilitar a instância padrão definindo `VSG_NODEFAULT_INSTANCE` para evitar a sobrecarga.  
  
 Se a instância padrão não for desabilitada, ele é inicializado automaticamente antes da execução do seu programa e é destruído automaticamente quando seu programa é encerrado. Não é preciso inicializar ou não a essa instância explicitamente.  
  
 Para desabilitar a instância padrão, você deve definir `VSG_NODEFAULT_INSTANCE` antes de incluir `vsgcapture.h` em seu programa.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como desabilitar a instância padrão:  
  
```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
