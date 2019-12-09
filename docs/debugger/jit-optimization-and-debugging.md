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
ms.openlocfilehash: 12752acf75da70fa30666f9b1780256c94bde859
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731618"
---
# <a name="jit-optimization-and-debugging"></a>Otimização e depuração JIT
**Como as otimizações funcionam no .net:** Se você estiver tentando depurar o código, será mais fácil quando esse código **não** for otimizado. Isso ocorre porque, quando o código é otimizado, o compilador e o tempo de execução fazem alterações no código de CPU emitido para que ele seja executado mais rapidamente, mas tem um mapeamento menos direto para o código-fonte original. Isso significa que os depuradores geralmente não conseguem informar o valor das variáveis locais, e a depuração de código e os pontos de interrupção podem não funcionar conforme o esperado.

Normalmente, a configuração de Build de versão cria código otimizado e a configuração de compilação de depuração não. A propriedade `Optimize` MSBuild controla se o compilador é instruído a otimizar o código.

No ecossistema do .NET, o código é retirado das instruções de origem para a CPU em um processo de duas C# etapas: primeiro, o compilador converte o texto que você digita em um formato binário intermediário chamado MSIL e grava isso em arquivos. dll. Posteriormente, o tempo de execução do .NET Converte essa MSIL em instruções de CPU. Ambas as etapas podem otimizar para algum grau, mas a segunda etapa executada pelo tempo de execução do .NET executa as otimizações mais significativas.

**A opção ' suprimir otimização JIT na carga do módulo (somente gerenciado) ':** O depurador expõe uma opção que controla o que acontece quando uma DLL que é compilada com otimizações habilitadas carrega dentro do processo de destino. Se essa opção estiver desmarcada (o estado padrão), quando o tempo de execução do .NET compilar o código MSIL no código de CPU, ele deixará as otimizações habilitadas. Se a opção estiver marcada, o depurador solicitará que as otimizações sejam desabilitadas.

Para localizar a opção **suprimir otimização JIT na carga do módulo (somente gerenciado)** , selecione **ferramentas** > **Opções**e, em seguida, selecione a página **geral** no nó **depuração** .

**Quando você deve marcar esta opção:** Marque essa opção quando você baixou as DLLs de outra fonte, como um pacote NuGet, e deseja depurar o código nessa DLL. Para que isso funcione, você também deve encontrar o arquivo de símbolo (. pdb) para essa DLL.

Se você estiver interessado apenas em depurar o código que está compilando localmente, é melhor deixar essa opção desmarcada, como, em alguns casos, habilitar essa opção reduzirá significativamente a depuração. Há duas razões para isso causar lentidão:

* O código otimizado é executado mais rapidamente. Se você estiver desligando otimizações para muitos códigos, o impacto no desempenho poderá ser somado.
* Se você tiver Apenas Meu Código habilitados, o depurador não tentará nem carregará símbolos para DLLs otimizadas. Encontrar símbolos pode levar muito tempo.

**Limitações desta opção:** Há duas situações em que essa opção **não** funcionará:

1. Em situações em que você está anexando o depurador a um processo já em execução, essa opção não terá nenhum efeito em módulos que já foram carregados no momento em que o depurador foi anexado.
2. Essa opção não tem efeito em DLLs que foram previamente compiladas (a. k. a ngen'ed) para o código nativo. No entanto, você pode desabilitar o uso do código pré-compilado iniciando o processo com a variável de ambiente ' COMPlus_ZapDisable ' definida como ' 1 '.

## <a name="see-also"></a>Consulte também
- [Depurando código gerenciado](../debugger/debugging-managed-code.md)
- [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)
- [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Processo de execução gerenciada](/dotnet/standard/managed-execution-process)
