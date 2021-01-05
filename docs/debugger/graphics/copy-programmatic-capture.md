---
title: Cópia (captura programática) | Microsoft Docs
description: Use o método Copy da classe VsgDbg para copiar o conteúdo do arquivo de log de gráficos ativo (. vsglog) em um novo arquivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727838"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura programática)
Copia o conteúdo do arquivo de log de gráficos ativo (. vsglog) em um novo arquivo.

## <a name="syntax"></a>Sintaxe

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Parâmetros
 `szNewVSGLog` O nome de arquivo do novo arquivo de log de gráficos.

## <a name="remarks"></a>Comentários
 Para copiar as informações de gráficos para um novo arquivo, você já deve ter capturado algumas informações gráficas; caso contrário, nada acontece.