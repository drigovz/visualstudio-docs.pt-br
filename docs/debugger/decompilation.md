---
title: Descompilar código .NET durante a depuração | Microsoft Docs
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
ms.openlocfilehash: ffd5f2e4bfc13f79b519fbdf9b3cf517793cd324
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091929"
---
# <a name="generate-source-code-from-net-assemblies-while-debugging"></a>Gerar código-fonte de assemblies do .NET durante a depuração

Ao depurar um aplicativo .NET, você pode achar que deseja exibir o código-fonte que você não tem. Por exemplo, dividindo uma exceção ou usando a pilha de chamadas para navegar até um local de origem.

> [!NOTE]
> * A geração de código-fonte (descompilação) só está disponível para aplicativos .NET e é baseada no projeto [ILSpy](https://github.com/icsharpcode/ILSpy) de código-fonte aberto.
> * A descompilação só está disponível no Visual Studio 2019 16,5 e posterior.

## <a name="generate-source-code"></a>Gerar código-fonte

Quando você estiver Depurando e nenhum código-fonte estiver disponível, o Visual Studio mostrará o documento de **origem não encontrado** ou, se você não tiver símbolos para o assembly, o documento **nenhum símbolo carregado** . Ambos os documentos têm uma opção de **código-fonte de descompilação** que gera C# código para o local atual. O código C# gerado pode ser usado assim como qualquer outro código-fonte. Você pode exibir o código, inspecionar variáveis, definir pontos de interrupção e assim por diante.

### <a name="no-symbols-loaded"></a>Nenhum símbolo carregado

A ilustração a seguir mostra a mensagem **nenhum símbolo carregado** .

![Captura de tela sem documento carregado de símbolo](media/decompilation-no-symbol-found.png)

### <a name="source-not-found"></a>Origem não encontrada

A ilustração a seguir mostra a mensagem **fonte não encontrada** .

![Captura de tela do documento fonte não encontrada](media/decompilation-no-source-found.png)

## <a name="generate-and-embed-sources-for-an-assembly"></a>Gerar e inserir fontes para um assembly

Além de gerar o código-fonte para um local específico, você pode gerar todo o código-fonte para um determinado assembly .NET. Para fazer isso, vá para a janela **módulos** e, no menu de contexto de um assembly .net, e selecione o comando **descompilar código-fonte** . O Visual Studio gera um arquivo de símbolo para o assembly e, em seguida, insere a origem no arquivo de símbolo. Em uma etapa posterior, você pode [extrair](#extract-and-view-the-embedded-source-code) o código-fonte incorporado.

![Captura de tela do menu de contexto do assembly na janela de módulos com o comando de origem de descompilação.](media/decompilation-decompile-source-code.png)

## <a name="extract-and-view-the-embedded-source-code"></a>Extrair e exibir o código-fonte inserido

Você pode extrair os arquivos de origem inseridos em um arquivo de símbolo usando o comando **extrair código-fonte** no menu de contexto da janela **módulos** .

![Captura de tela do menu de contexto do assembly na janela de módulos com o comando extrair fontes.](media/decompilation-extract-source-code.png)

Os arquivos de origem extraídos são adicionados à solução como [arquivos diversos](../ide/reference/miscellaneous-files.md). O recurso de arquivos diversos está desativado por padrão no Visual Studio. Você pode habilitar esse recurso nas **ferramentas** > **opções** > **ambiente** > **documentos** > **Mostrar arquivos diversos na caixa de seleção Gerenciador de soluções** . Sem habilitar esse recurso, você não poderá abrir o código-fonte extraído.

![Captura de tela da página opção de ferramentas com a opção diversos arquivos habilitada.](media/decompilation-tools-options-misc-files.png)

Os arquivos de origem extraídos aparecem nos arquivos diversos em **Gerenciador de soluções**.

![Captura de tela do Gerenciador de soluções com arquivos diversos.](media/decompilation-solution-explorer.png)

## <a name="known-limitations"></a>Limitações conhecidas

### <a name="requires-break-mode"></a>Requer o modo de interrupção

A geração do código-fonte usando a descompilação só é possível quando o depurador está no modo de interrupção e o aplicativo é pausado. Por exemplo, o Visual Studio entra no modo de interrupção quando atinge um ponto de interrupção ou uma exceção. Você pode facilmente disparar o Visual Studio para interromper na próxima vez em que seu código for executado usando o comando **Break All** (![ícone interromper tudo](media/decompilation-break-all.png)).

### <a name="decompilation-limitations"></a>Limitações de descompilação

A geração do código-fonte do formato intermediário (IL) usado em assemblies .NET tem algumas limitações inerentes. Como tal, o código-fonte gerado não se parece com o código-fonte original. A maioria das diferenças é em locais onde as informações no código-fonte original não são necessárias no tempo de execução. Por exemplo, informações como espaço em branco, comentários e nomes de variáveis locais não são necessárias em tempo de execução. Recomendamos que você use a origem gerada para entender como o programa está em execução e não como uma substituição para o código-fonte original.

### <a name="debug-optimized-or-release-assemblies"></a>Depurar assemblies otimizados ou de versão

Ao depurar o código que foi descompilado de um assembly que foi compilado usando otimizações do compilador, você pode ter os seguintes problemas:
- Os pontos de interrupção nem sempre podem ser associados ao local de fornecimento correspondente.
- A depuração pode nem sempre passar para o local correto.
- As variáveis locais podem não ter nomes precisos.

Mais detalhes podem ser encontrados no problema do GitHub: [integração do IChsarpCompiler. decompilador ao depurador do vs](https://github.com/icsharpcode/ILSpy/issues/1901).

### <a name="extracted-sources"></a>Fontes extraídas

O código-fonte extraído de um assembly tem as seguintes limitações:
- O nome e o local dos arquivos gerados não são configuráveis.
- Os arquivos são temporários e serão excluídos pelo Visual Studio.
- Os arquivos são colocados em uma única pasta e qualquer hierarquia de pastas que as fontes originais tinham não ser usada.
- O nome de arquivo para cada arquivo contém um hash de soma de verificação do arquivo.

### <a name="generated-code-is-c-only"></a>O código gerado C# só é
A descompilação gera apenas arquivos de código C#-fonte no. Não há nenhuma opção para gerar arquivos em qualquer outro idioma.