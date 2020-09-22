---
title: Realocar binários instrumentados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 13fa5c3413e620e43a695e205a0523dce23e90b4
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851340"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Como realocar binários instrumentados

Durante a instrumentação, as investigações são inseridas no binário para medir o desempenho do aplicativo. Ao escolher realocar o binário instrumentado, uma cópia do binário original é instrumentada e colocada no local especificado. Essa opção será útil se você não quiser que o criador de perfil renomeie o binário original. Se o binário não for realocado, a versão original do binário será substituída.

## <a name="to-relocate-instrumented-binary"></a>Para realocar binários instrumentados

1. Em **Gerenciador de desempenho**, clique com o botão direito do mouse na sessão de desempenho e clique em **Propriedades**.

2. Nas **Páginas de propriedades**, clique nas propriedades do **Binário**.

3. Selecione a caixa de seleção **Realocar binários instrumentados**.

4. Especifique o local para o binário instrumentado.

## <a name="see-also"></a>Confira também

[Configurar sessões](../profiling/configuring-performance-sessions.md) 
 de desempenho [VSInstr](../profiling/vsinstr.md)
