---
title: Otimização e depuração JIT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae11860aaa64448cd4d23b5602cf4c2da1575ce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916212"
---
# <a name="jit-optimization-and-debugging"></a>Otimização e depuração JIT
Se você estiver tentando depurar o código, será mais fácil quando esse código **não** for otimizado. Quando o código é otimizado, o compilador e o tempo de execução fazem alterações no código de CPU emitido para que ele seja executado mais rapidamente, mas tem um mapeamento menos direto para o código-fonte original. Se o mapeamento for menos direto, os depuradores geralmente não poderão informar o valor das variáveis locais, e a depuração de código e os pontos de interrupção talvez não funcionem conforme o esperado.

> [!NOTE]
> Para obter mais informações sobre a depuração JIT (just in time), leia [esta documentação](../debugger/debug-using-the-just-in-time-debugger.md).

## <a name="how-optimizations-work-in-net"></a>Como as otimizações funcionam no .NET 
Normalmente, a configuração de Build de versão cria código otimizado e a configuração de compilação de depuração não. A `Optimize` Propriedade MSBuild controla se o compilador é instruído a otimizar o código.

No ecossistema do .NET, o código é retirado das instruções de origem para a CPU em um processo de duas etapas: primeiro, o compilador C# converte o texto que você digita em um formato binário intermediário chamado MSIL e grava o MSIL em arquivos. dll. Posteriormente, o tempo de execução do .NET Converte essa MSIL em instruções de CPU. Ambas as etapas podem otimizar para algum grau, mas a segunda etapa executada pelo tempo de execução do .NET executa as otimizações mais significativas.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>A opção ' suprimir otimização JIT na carga do módulo (somente gerenciado) '
O depurador expõe uma opção que controla o que acontece quando uma DLL que é compilada com otimizações habilitadas carrega dentro do processo de destino. Se essa opção estiver desmarcada (o estado padrão), quando o tempo de execução do .NET compilar o código MSIL no código de CPU, ele deixará as otimizações habilitadas. Se a opção estiver marcada, o depurador solicitará que as otimizações sejam desabilitadas.

Para localizar a opção **suprimir otimização JIT na carga do módulo (somente gerenciado)** , selecione opções de **ferramentas**  >  **Options**e, em seguida, selecione a página **geral** no nó **depuração** .

![Suprimir otimização JIT](../debugger/media/suppress-jit-tool-options.png "Suprimir otimização JIT")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>Quando você deve marcar a opção ' suprimir a otimização JIT '?
Marque essa opção quando você baixou as DLLs de outra fonte, como um pacote NuGet, e deseja depurar o código nessa DLL. Para que a supressão funcione, você também deve encontrar o arquivo de símbolo (. pdb) para essa DLL.

Se você estiver interessado apenas em depurar o código que está compilando localmente, é melhor deixar essa opção desmarcada, como, em alguns casos, habilitar essa opção reduzirá significativamente a depuração. Há dois motivos para isso causar lentidão:

* O código otimizado é executado mais rapidamente. Se você estiver desligando otimizações para muitos códigos, o impacto no desempenho poderá ser somado.
* Se você tiver Apenas Meu Código habilitados, o depurador nem mesmo tentará carregar símbolos para DLLs otimizadas. Encontrar símbolos pode levar muito tempo.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>Limitações da opção ' suprimir a otimização JIT ' 
Há duas situações em que ativar essa opção **não** funcionará:

1. Em situações em que você está anexando o depurador a um processo já em execução, essa opção não terá nenhum efeito em módulos que já foram carregados no momento em que o depurador foi anexado.
2. Essa opção não tem efeito em DLLs que foram previamente compiladas (a. k. a ngen'ed) para o código nativo. No entanto, você pode desabilitar o uso do código pré-compilado iniciando o processo com a variável de ambiente **' COMPlus_ReadyToRun '** definida como **' 0 '**. Isso informará ao tempo de execução do .NET Core para desabilitar o uso de imagens pré-compiladas, forçando o tempo de execução para o código de estrutura de compilação JIT. 

    > [!IMPORTANT]
    > Se você estiver visando .NET Framework ou uma versão mais antiga do .NET Core (2. x ou inferior), adicione também a variável de ambiente ' COMPlus_ZapDisable ' e defina-a como ' 1 '

    **Para definir uma variável de ambiente para um projeto do .NET Core no Visual Studio:**
    1. Na **Gerenciador de soluções**, **clique com o botão direito do mouse** no arquivo de projeto e selecione **Propriedades**.
    2. Navegue até a guia **depurar** e, em **variáveis de ambiente**, clique no botão **Adicionar** .
    3. Defina o nome (chave) para **COMPlus_ReadyToRun** e defina o valor como **0**.

    ![Definir COMPlus_ReadyToRun variável de ambiente](../debugger/media/environment-variables-debug-menu.png "Definir COMPlus_ReadyToRun variável de ambiente")

## <a name="see-also"></a>Confira também
- [Como depurar a origem do DOTNET Framework](../debugger/how-to-debug-dotnet-framework-source.md)
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
- [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Anexar aos processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processo de execução gerenciada](/dotnet/standard/managed-execution-process)
