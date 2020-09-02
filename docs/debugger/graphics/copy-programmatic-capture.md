---
title: Cópia (captura programática) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895948"
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