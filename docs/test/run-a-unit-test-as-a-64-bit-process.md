---
title: Executar um teste de unidade como um processo de 64 bits
ms.date: 03/10/2020
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d6c6839f8c4702d88d1022116231c6f22b5dbf21
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093915"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>Executar um teste de unidade como um processo de 64 bits

Se você tiver um computador de 64 bits, você poderá executar testes de unidade e capturar informações de cobertura de código como um processo de 64 bits.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>Para executar de um teste de unidade como um processo de 64 bits

1. Se seu código ou testes foram compilados como 32 bits/x86, mas agora você quer executá-los como um processo de 64 bits, recompile-os como **Qualquer CPU**.

   ::: moniker range="vs-2017"
   Alternativamente, no Visual Studio 2017, você também pode compilar seu projeto como **64 bits**.
   ::: moniker-end

    > [!TIP]
    > Para a máxima flexibilidade, compile seus projetos de teste com a configuração **Qualquer CPU**. Em seguida, você poderá executar os agentes de 32 bits e de 64 bits. Não há vantagem em compilar projetos de teste com a configuração de **64 bits**.

2. Defina os testes unitários como um processo de 64 bits.

   ::: moniker range=">=vs-2019"
   No menu Visual Studio, escolha **Teste**e escolha **Arquitetura do processador para projetos AnyCPU**. Escolha **x64** para executar os testes como um processo de 64 bits.
   ::: moniker-end
   ::: moniker range="vs-2017"
   No menu Visual Studio, escolha **'Teste'** e escolha **'Configurações de teste'** e escolha **'Arquitetura do processador'.** Escolha **x64** para executar os testes como um processo de 64 bits.
   ::: moniker-end

   \- ou –

   Especifique `<TargetPlatform>x64</TargetPlatform>` em um arquivo *.runsettings.* Uma vantagem desse método é que você pode especificar grupos de configurações em arquivos diferentes e mudar rapidamente entre diferentes configurações. Você também pode copiar as configurações entre soluções. Para obter mais informações, consulte [Configurar testes de unidade usando um arquivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

## <a name="see-also"></a>Confira também

- [Execução de testes de unidade com o gerenciador de testes](../test/run-unit-tests-with-test-explorer.md)
- [Unidade teste seu código](../test/unit-test-your-code.md)
