---
title: UnInit | Microsoft Docs
description: Use o método uninit () de VsgDbg para finalizar e fechar o arquivo de log de gráficos e para liberar recursos de registro em log.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905013"
---
# <a name="uninit"></a>UnInit
Finaliza o arquivo de log de gráficos, fecha-o e libera os recursos que foram usados enquanto o aplicativo gravava informações gráficas ativamente.

## <a name="syntax"></a>Sintaxe

```C++
void UnInit();
```

## <a name="remarks"></a>Comentários
 `UnInit` é chamado automaticamente quando uma instância da `VsgDbg` classe é destruída. Se a `VsgDbg` instância não estiver gravando ativamente as informações gráficas, isso não terá efeito.

 Depois de `UnInit` ter sido chamado em uma instância da `VsgDbg` classe, um novo arquivo de log de elementos gráficos pode ser criado chamando `Init` e finalizado chamando `UnInit` . Você pode repetir isso quantas vezes quiser usar a mesma `VsgDbg` instância para criar vários arquivos de log de gráficos independentes.

## <a name="see-also"></a>Confira também
- [Init](init.md)