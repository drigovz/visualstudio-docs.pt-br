---
title: Caixa de diálogo de Just-In-Time, depuração, opções | Microsoft Docs
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
ms.openlocfilehash: 23a285cf0ce017130a5fe76171c50082362e4856
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905929"
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

 **Outro depurador se registrou como depurador Just-In-Time. Para reparar, habilite a depuração Just-In-Time ou execute o reparo do Visual Studio.**

 Essa mensagem ocorrerá se você tiver outro depurador, possivelmente uma versão anterior do depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], definida como o depurador Just-In-Time.

 Outra mensagem que você pode ver é o seguinte:

 **Erros do registro de depuração Just-In-Time detectados. Para reparar, habilite a depuração Just-In-Time ou execute o reparo do Visual Studio.**

 Se você vir qualquer um desses avisos, a depuração Just-In-Time com o [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] exigirá privilégios de administrador até você solucionar o problema. Se você tentar habilitar como um não administrador nessas condições, verá a seguinte mensagem de erro:

 **Acesso negado. Faça um administrador habilitar a depuração Just-In-Time ou reparar a instalação do Visual Studio.**

## <a name="see-also"></a>Consulte também
- [Caixa de diálogo Depuração, Opções](../debugger/debugging-options-dialog-box.md)
- [Como: Especificar as configurações do depurador](../debugger/how-to-specify-debugger-settings.md)