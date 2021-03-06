---
title: Depurar testes de unidade com o Gerenciador de Testes
description: Saiba como depurar testes de unidade com o Gerenciador de testes no Visual Studio.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09889839c9e2873810c78a5f0c3425820170b68d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964375"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>Depurar e analisar testes de unidade com o Gerenciador de testes

Você pode usar o Gerenciador de Testes para iniciar uma sessão de depuração para os testes. Passar pelo código com o depurador do Visual Studio permite-lhe navegar facilmente entre os testes de unidade e o projeto sendo testado. Para iniciar a depuração:

1. No editor do Visual Studio, defina um ponto de interrupção em um ou mais métodos de teste que deseje depurar.

    > [!NOTE]
    > Como os métodos de teste podem ser executados em qualquer ordem, defina pontos de interrupção em todos os métodos de teste que deseje depurar.

::: moniker range="vs-2017"
2. No Gerenciador de testes, selecione os métodos de teste e, em seguida, escolha **depurar testes selecionados** no menu do botão direito do mouse.
::: moniker-end
::: moniker range=">=vs-2019"
2. No Gerenciador de testes, selecione os métodos de teste e, em seguida, escolha **depurar** no menu do botão direito do mouse.

   ![Detalhes da execução do teste](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   Para obter mais informações sobre o depurador, confira [Depuração no Visual Studio](../debugger/debugger-feature-tour.md).

## <a name="diagnose-test-method-performance-issues"></a>Diagnosticar problemas de desempenho do método de teste

::: moniker range="vs-2017"
Para diagnosticar por que um método de teste está demorando para ser executado, selecione o método no Gerenciador de Testes e, em seguida, escolha **Analisar o Teste Selecionado** no menu de clique com o botão direito. Consulte [relatório de criação de perfil de instrumentação](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

::: moniker range=">=vs-2019"
Para diagnosticar por quê um método de teste está demorando para ser executado, selecione o método no Gerenciador de Testes e, em seguida, escolha **Perfil** no menu do clique com o botão direito. Consulte [relatório de criação de perfil de instrumentação](../profiling/understanding-instrumentation-data-values.md?view=vs-2017&preserve-view=true).
::: moniker-end

> [!NOTE]
> Atualmente, não há suporte para esse recurso no .NET Core.

## <a name="see-also"></a>Confira também

- [Teste de unidade em seu código](../test/unit-test-your-code.md)
- [Executar testes de unidade com o Gerenciador de Testes](../test/run-unit-tests-with-test-explorer.md)
- [Perguntas Frequentes sobre o Gerenciador de Testes](test-explorer-faq.md)
