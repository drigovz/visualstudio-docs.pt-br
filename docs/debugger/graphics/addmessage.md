---
title: AddMessage | Microsoft Docs
description: Use o Método AddMessage da classe VsgDbg para adicionar uma mensagem personalizada à tela de Head-Up de diagnóstico de gráficos (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874633"
---
# <a name="addmessage"></a>AddMessage
Adiciona uma mensagem personalizada ao *HUD* de diagnóstico de gráficos (exibição de cabeçalho).

## <a name="syntax"></a>Sintaxe

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parâmetros
 `szMessage` A mensagem a ser adicionada ao HUD.

## <a name="remarks"></a>Comentários
 O HUD de diagnóstico de gráficos é exibido no canto superior esquerdo do aplicativo que está sendo executado em diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e mensagens que são adicionadas chamando essa função.

 Para adicionar uma mensagem ao HUD, você não precisa estar ativamente capturando informações gráficas, ou seja, uma mensagem pode ser adicionada por meio de uma instância da `VsgDbg` classe, mas a função de membro [init](init.md) não deve ser chamada primeiro. As mensagens são exibidas apenas no HUD, elas não são registradas no arquivo de log de gráficos.