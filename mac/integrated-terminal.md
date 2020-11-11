---
title: Visual Studio para Mac – terminal integrado
description: Trabalhando com o terminal integrado no Visual Studio para Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/14/2020
ms.assetid: EFD53CE9-8174-4FE4-8863-2984D22FD921
ms.openlocfilehash: f91c2b1c3f06f8f1fbe54e32fde70b9fe88c5f5d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492861"
---
# <a name="integrated-terminal"></a>Terminal Integrado
No Visual Studio para Mac você pode abrir uma janela de terminal integrada, começando inicialmente na raiz da sua solução. O terminal pode ser útil para diferentes tipos de situações – executando tarefas de front-end (por exemplo: NPM, ng ou Vue), gerenciando contêineres, executando comandos git avançados, executando comandos de Entity Framework, exibindo a saída da CLI dotnet, adicionando pacotes NuGet e muito mais. 

Para abrir o terminal:
- Use o atalho de teclado **Ctrl + '** para mostrar ou ocultar a janela do terminal.
- Use o menu **Exibir** \> **terminal** .
- Use o comando **terminal** da barra de pesquisa.

![* O terminal integrado Visual Studio para Mac imediatamente após ser iniciado. *](media/integrated-terminal-intro.png)

Por padrão, quando o terminal for iniciado, ele será:
- Defina o diretório de trabalho como o caminho da solução atual.
- Carregue o Shell do sistema padrão.

## <a name="search"></a>Search
Você pode pesquisar o conteúdo da janela do terminal usando o menu **pesquisar > localizar...** .

![* Experiência de pesquisa no terminal integrado Visual Studio para Mac *](media/integrated-terminal-search.png)

## <a name="terminal-keyboard-shortcuts"></a>Atalhos de teclado do terminal
|Comandos|Atalhos do teclado|
|-|-|
|Mostrar/ocultar a janela do terminal|**CTRL + '**|
|Criar nova instância de terminal|**CTRL + '**|
|Rolar página para cima|**PageUp**|
|Rolar página para baixo|**PageDown**|
|Percorrer comandos usados anteriormente|**↑** , **↓**|
|Aumentar tamanho da fonte|**⌘ +**|
|Diminuir tamanho da fonte|**⌘-**|

## <a name="multiple-instances"></a>Várias instâncias
Várias instâncias do terminal podem estar em execução a qualquer momento. Você pode criar uma nova instância usando o atalho de teclado **Ctrl + '** . Você pode alternar entre instâncias clicando na guia para cada instância ou usando o atalho **Ctrl + Tab** para usar a caixa de diálogo Seletor de janela.

![* Várias instâncias de terminal no Visual Studio para Mac *](media/integrated-terminal-multiple-instances.png) 

## <a name="customizing-the-terminal-window"></a>Personalizando a janela do terminal
### <a name="configuring-the-terminal-font"></a>Configurando a fonte do terminal
Você pode alterar a fonte e o tamanho usados para o conteúdo do terminal no painel preferências > ambiente > fontes. Por padrão, a fonte será a mesma que Janela de Saída conteúdo, usando Menlo regular, tamanho 11. Você pode defini-lo como qualquer fonte, independentemente da sua fonte do editor.

![* Personalizando as configurações de fonte para o terminal integrado *](media/integrated-terminal-change-font.png)

### <a name="reusing-system-terminal-customizations"></a>Reutilizando personalizações do terminal do sistema
O terminal integrado usa os mesmos padrões e configuração que o terminal do sistema macOS. Isso significa que as personalizações do terminal (zsh, Oh-My-zsh, etc.) também funcionam no terminal integrado.
