---
title: Descompilar o código .NET durante a depuração | Microsoft Docs
ms.date: 2/2/2020
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- decompilation, debugger, exception
- debugging [Visual Studio], decompilation, source not found
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: d63c05120842d52dd54359e128d0cc5f2a195817
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508739"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Gerar código-fonte a partir de conjuntos .NET durante a depuração

Ao depurar um aplicativo .NET, você pode descobrir que deseja visualizar o código-fonte que você não tem. Por exemplo, quebrar uma exceção ou usar a pilha de chamadas para navegar até um local de origem.

> [!NOTE]
> * A geração de código-fonte (descompilação) está disponível apenas para aplicativos .NET e é baseada no projeto [ILSpy](https://github.com/icsharpcode/ILSpy) de código aberto.
> * Decompilation só está disponível no Visual Studio 2019 16.5 e posterior.
> * A aplicação do [atributo SuppressIldasmAttribute](https://docs.microsoft.com/dotnet/api/system.runtime.compilerservices.suppressildasmattribute) a um conjunto ou módulo impede o Visual Studio de tentar descompilação.

## <a name="generate-source-code"></a>Gerar código-fonte

Quando você está depurando e nenhum código fonte está disponível, o Visual Studio mostra o documento **Fonte Não Encontrado** ou se você não tiver símbolos para a montagem, o documento **Sem Símbolos Carregados.** Ambos os documentos têm uma opção **de código-fonte Decompilaque** gera código C# para a localização atual. O código C# gerado pode então ser usado como qualquer outro código fonte. Você pode visualizar o código, inspecionar variáveis, definir pontos de interrupção e assim por diante.

### <a name="no-symbols-loaded"></a>Sem símbolos carregados

A ilustração a seguir mostra a mensagem **Sem Símbolos Carregados.**

![Captura de tela de nenhum documento carregado de símbolo](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Fonte não encontrada

A ilustração a seguir mostra a mensagem **Fonte Não Encontrada.**

![Captura de tela de origem não encontrada documento](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Gerar e incorporar fontes para uma montagem

Além de gerar código fonte para um local específico, você pode gerar todo o código fonte para um determinado conjunto .NET. Para fazer isso, vá para a janela **Módulos** e no menu de contexto de um conjunto .NET e selecione o comando **Decompile source code.** O Visual Studio gera um arquivo símbolo para a montagem e, em seguida, incorpora a fonte no arquivo símbolo. Em uma etapa posterior, você pode [extrair](#extract-and-view-the-embedded-source-code) o código fonte incorporado.

![Captura de tela do menu de contexto de montagem na janela módulos com comando de fonte descompilação.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrair e visualizar o código-fonte incorporado

Você pode extrair arquivos de origem que estão incorporados em um arquivo símbolo usando o comando **Extrato código-fonte** no menu de contexto da janela **Módulos.**

![Captura de tela do menu de contexto de montagem na janela módulos com comando extract sources.](media/decompilation-extract-source-code.png)

Os arquivos de origem extraídos são [adicionados](../ide/reference/miscellaneous-files.md)à solução como arquivos diversos . O recurso de arquivos diversos está desligado por padrão no Visual Studio. Você pode habilitar esse recurso a partir do **Ambiente de Ferramentas** > **Options** > **Documentos** > **do Ambiente** > Mostrar Arquivos Diversos na caixa de seleção**do Solution Explorer.** Sem habilitar esse recurso, você não poderá abrir o código fonte extraído.

![Captura de tela da página de opção de ferramentas com opção de arquivos diversos ativado.](media/decompilation-tools-options-misc-files.png)

Arquivos de origem extraídos aparecem nos arquivos diversos no **Solution Explorer**.

![Captura de tela do explorador de soluções com arquivos diversos.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="requires-break-mode"></a>Requer modo de quebra

A geração de código-fonte usando a compilação só é possível quando o depurador está no modo de quebra e o aplicativo é pausado. Por exemplo, o Visual Studio entra no modo de quebra quando atinge um ponto de ruptura ou uma exceção. Você pode facilmente acionar o Visual Studio para quebrar a próxima![vez](media/decompilation-break-all.png)que seu código é executado usando o comando **Break All** (Break all icon).

### <a name="decompilation-limitations"></a>Limitações de descompilação

A geração de código-fonte a partir do formato intermediário (IL) que é usado em conjuntos .NET tem algumas limitações inerentes. Como tal, o código-fonte gerado não se parece com o código fonte original. A maioria das diferenças estão em lugares onde as informações no código-fonte original não são necessárias em tempo de execução. Por exemplo, informações como espaço em branco, comentários e nomes de variáveis locais não são necessárias em tempo de execução. Recomendamos que você use a fonte gerada para entender como o programa está sendo executado e não como um substituto para o código fonte original.

### <a name="debug-optimized-or-release-assemblies"></a>Depuração otimizada ou lançamento de montagens

Ao depurar o código que foi descompilado de um conjunto que foi compilado usando otimizações de compiladores, você pode se deparar com os seguintes problemas:
- Os pontos de interrupção podem nem sempre se ligar ao local de sourcing correspondente.
- A pisada pode nem sempre passar para o local correto.
- As variáveis locais podem não ter nomes precisos.
- Algumas variáveis podem não estar disponíveis para avaliação.

Mais detalhes podem ser encontrados no problema do GitHub: [integração ICSharpCode.Decompiler no VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="decompilation-reliability"></a>Confiabilidade da compilação

Uma porcentagem relativamente pequena de tentativas de descompilação pode resultar em falha. Isso é devido a um erro de referência nulo de ponto de seqüência no ILSpy.  Nós mitigamos o fracasso pegando essas questões e falhando graciosamente na tentativa de descompilação.

Mais detalhes podem ser encontrados no problema do GitHub: [integração ICSharpCode.Decompiler no VS Debugger](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="limitations-with-async-code"></a>Limitações com código assíncrono

Os resultados de descompilação de módulos com padrões de código assincronico/espera podem estar incompletos ou falhar completamente. A implementação do ILSpy de máquinas de estado de async/aguardar e produzir apenas parcialmente implementadas. 

Mais detalhes podem ser encontrados no problema do GitHub: [PDB Generator Status](https://github.com/icsharpcode/ILSpy/issues/1422).

### <a name="just-my-code"></a>Apenas Meu Código

As configurações [do Just My Code (JMC)](https://docs.microsoft.com/visualstudio/debugger/just-my-code) permitem que o Visual Studio ultrapasse o sistema, a estrutura, a biblioteca e outras chamadas não-usuários. Durante uma sessão de depuração, a janela **Módulos** mostra quais módulos de código o depurador está tratando como Meu Código (código do usuário).

A descompilação de módulos otimizados ou de lançamento produz código não-usuário. Se o depurador quebrar seu código não-usuário descompilado, por exemplo, a janela **Sem Origem** será exibida. Para desativar Just My Code, navegue até as**opções** **de ferramentas** > (ou **depuração** > **de opções)**> **Depuração** > **Geral**e, em seguida, desmarque Ativar apenas **meu código**.

### <a name="extracted-sources"></a>Fontes extraídas

O código-fonte extraído de um conjunto tem as seguintes limitações:
- O nome e a localização dos arquivos gerados não são configuráveis.
- Os arquivos são temporários e serão excluídos pelo Visual Studio.
- Os arquivos são colocados em uma única pasta e qualquer hierarquia de pasta que as fontes originais tinham não é usada.
- O nome do arquivo para cada arquivo contém um hash de soma de cheques do arquivo.

### <a name="generated-code-is-c-only"></a>O código gerado é c# apenas
Decompilação só gera arquivos de código-fonte em C#. Não há opção de gerar arquivos em qualquer outro idioma.
