---
title: Processar o Gerenciador de depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- machine debug manager
- debugging [Debugging SDK], Machine Debug Manager
ms.assetid: d0861e0c-b819-490c-9604-5e6d08ac291a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f6a93cc87be2369ba3bc96bf6682caeb4a727c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889166"
---
# <a name="process-debug-manager"></a>O Gerenciador de depuração do processo
O Gerenciador de depuração do processo (PDM) é um componente do Visual Studio que gerencia os programas e processos, tornando-os disponíveis para a sessão de depuração manager e os mecanismos de depuração.

 O PDM gerencia todos os processos que podem ser depurados. Para ser depurado, um programa deve ser registrado com o PDM. Esse registro é feito no momento em que o programa é iniciado por uma porta ou um mecanismo de depuração.

## <a name="see-also"></a>Consulte também
- [Processos](../../extensibility/debugger/processes.md)
- [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)
- [Portas](../../extensibility/debugger/ports.md)
- [Programas](../../extensibility/debugger/programs.md)
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)