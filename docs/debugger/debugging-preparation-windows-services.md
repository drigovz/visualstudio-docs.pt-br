---
title: Preparar para depurar serviços do Windows | Microsoft Docs
description: Prepare-se para depurar os serviços do Windows, que são programas executados em segundo plano no Windows, no Visual Studio.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Windows services
- Windows Service applications, debugging
ms.assetid: ac0a99f7-ec3d-4a20-b17f-698a817fdcc2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fe922106181633f506147decc3b578e7dc6e704
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728207"
---
# <a name="debugging-preparation-windows-services"></a>Preparação de depuração: Serviços Windows
Um serviço do Windows é um programa executado em segundo plano no Microsoft Windows. Os exemplos incluem o serviço de Telnet e o serviço de tempo do Windows, que atualiza o relógio visível do computador. Um serviço do Windows não pode ser executados no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]; ele deve ser executado no contexto do Gerenciador de Controle de Serviços. Para obter mais informações, confira [Criando serviços do Windows](/dotnet/framework/windows-services/how-to-create-windows-services), [Depurando aplicativos de serviço Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) e [Aplicativos de serviço Windows](/dotnet/framework/windows-services/index).

## <a name="see-also"></a>Consulte também
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
- [Tipos de projeto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configurações de projeto para configurações de depuração em C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Configurações de projeto para uma configuração de depuração de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Como depurar o método OnStart](../debugger/how-to-debug-the-onstart-method.md)