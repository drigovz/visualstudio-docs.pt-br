---
title: 'VsgDbg:: VsgDbg (Construtor) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae94a7cb9572a0975dc1c3717275c384c2e45978
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734754"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (Construtor)
Constrói uma instância da classe `VsgDbg` com ou sem preparar o componente no aplicativo de diagnóstico de gráficos para capturar e gravar ativamente informações de gráficos por padrão, com base no parâmetro booliano especificado.

## <a name="syntax"></a>Sintaxe

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Parâmetros
 `bDefaultInit` `true` para especificar que o componente no aplicativo do diagnóstico de gráficos seja preparado para capturar e registrar informações de gráficos ativamente;  `false` para especificar que o aplicativo não deve estar preparado para capturar e gravar informações de gráficos ativamente neste momento.

## <a name="remarks"></a>Comentários
 Quando o construtor é chamado com `bDefaultInit` definido como `true`, o nome de arquivo do arquivo de log de gráficos é determinado pelo modo como os símbolos de pré-processador `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME` são definidos antes que `vsgcapture.h` seja incluído em seu aplicativo.

 Quando o construtor é chamado com `bDefaultInit` definido como `false`, o componente no aplicativo do diagnóstico de gráficos pode ser preparado para capturar ativamente e gravar informações de gráficos em um momento posterior chamando a função `Init`.

## <a name="see-also"></a>Consulte também
- [VsgDbg::~VsgDbg (Destruidor)](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)