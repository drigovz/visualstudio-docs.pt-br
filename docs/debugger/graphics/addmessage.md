---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896348"
---
# <a name="addmessage"></a>AddMessage
Adiciona uma mensagem personalizada para o diagnóstico de gráficos *HUD* (Head-Up Display).

## <a name="syntax"></a>Sintaxe

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parâmetros
 `szMessage` A mensagem a ser adicionado ao HUD.

## <a name="remarks"></a>Comentários
 O HUD do diagnóstico de gráficos é exibida no canto superior esquerdo do aplicativo que está em execução no diagnóstico de gráficos. Ele exibe informações de tempo de execução sobre o aplicativo e sobre a captura de informações de gráficos e as mensagens que são adicionadas ao chamar essa função.

 Para adicionar uma mensagem para o HUD, você não precisa ser ativamente capturando informações de gráficos — ou seja, uma mensagem pode ser adicionada por meio de uma instância das `VsgDbg` classe, mas o [Init](init.md) função de membro não precisa ser chamado primeiro. As mensagens só são exibidas no HUD, eles não estão registrados no arquivo de log de gráficos.