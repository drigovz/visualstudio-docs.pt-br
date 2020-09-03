---
title: Caixa de diálogo depuração, opções just-in-time | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c27ec66c8165995c6877b9a9e65802813140c7f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731605"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>Caixa de diálogo Just-In-Time, Depuração, Opções
Para acessar a página **Just-In-Time**, vá até o menu **Ferramentas** e clique em **Opções**. Na caixa de diálogo **Opções**, expanda o nó **Depuração** e selecione **Just-In-Time**. Essa página permite habilitar a depuração Just-In-Time para o código gerenciado, o código nativo e o script. Para obter mais informações, confira [Depuração Just-In-Time](../debugger/just-in-time-debugging-in-visual-studio.md).

 Você pode habilitar a depuração Just-In-Time para estes tipos de programa:

- Gerenciado

- Nativo

- script

  A depuração Just-In-Time é uma técnica para depurar um programa que é iniciado fora do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você pode executar um programa criado no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fora do ambiente do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se você tiver habilitado a depuração Just-In-Time, uma falha exibirá uma caixa de diálogo que perguntará se você quer depurar.

## <a name="associated-warnings"></a>Avisos associados
 Quando você visita esta página da caixa de diálogo **Opções**, poderá ver uma mensagem de aviso assim:

 **Outro depurador se registrou como depurador just-in-time. Para reparar, habilite a depuração Just-in-time ou execute o reparo do Visual Studio.**

 Essa mensagem ocorrerá se você tiver outro depurador, possivelmente uma versão anterior do depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definida como o depurador Just-In-Time.

 Outra mensagem que você pode ver é o seguinte:

 **Erros de registro de depuração Just-in-time detectados. Para reparar, habilite a depuração Just-in-time ou execute o reparo do Visual Studio.**

 Se você vir qualquer um desses avisos, a depuração Just-In-Time com o [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] exigirá privilégios de administrador até você solucionar o problema. Se você tentar habilitar como um não administrador nessas condições, verá a seguinte mensagem de erro:

 **Acesso negado. Fazer com que um administrador habilite a depuração Just-in-time ou repare a instalação do Visual Studio.**

## <a name="see-also"></a>Confira também
- [Depurando, Caixa de Diálogo Opções](../debugger/debugging-options-dialog-box.md)
- [Como especificar configurações do depurador](../debugger/how-to-specify-debugger-settings.md)