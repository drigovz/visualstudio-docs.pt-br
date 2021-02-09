---
title: Criar XAML no Visual Studio e no Blend para Visual Studio
titleSuffix: ''
description: Saiba mais sobre os recursos das ferramentas de Design Visual no Visual Studio e Blend para Visual Studio para compilar a interface do usuário e experiências em XAML.
ms.custom: SEO-VS-2020
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: fc6c05b925c8dac5c488ce3eea79ca683b590b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876414"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Projetar XAML no Visual Studio e no Blend para Visual Studio

O Visual Studio e o Blend for Visual Studio fornecem ferramentas visuais para criar interfaces do usuário envolventes e experiências de mídia avançadas com XAML para vários tipos de aplicativos. Os dois IDEs (ambientes de desenvolvimento integrados) compartilham um conjunto comum de recursos, incluindo um editor XAML visual (o designer). O Blend para Visual Studio, que dá suporte às plataformas WPF e UWP, fornece ferramentas adicionais para a criação de estados visuais e animações.

É possível alternar entre o Visual Studio e o Blend para Visual Studio e até deixar o mesmo projeto aberto nos dois IDEs ao mesmo tempo. As alterações salvas nos arquivos XAML em um IDE podem ser aplicadas por meio de recarregamento automático ao mudar para o outro IDE. Você pode controlar o comportamento de recarregamento navegando até **ferramentas**  >  **Opções**  >    >  **documentos** de ambiente em qualquer IDE.

## <a name="installation"></a>Instalação

- Para criar aplicativos WPF, instale a carga de trabalho do **desenvolvimento de área de trabalho .NET** no Visual Studio. O Blend para Visual Studio também será instalado.

     ![Captura de tela da carga de trabalho de desenvolvimento do .NET desktop do Instalador do Visual Studio](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Para criar aplicativos UWP, instale a carga de trabalho de **desenvolvimento de Plataforma Universal do Windows** no Visual Studio. O Blend para Visual Studio também será instalado.

     ![Captura de tela da carga de trabalho de desenvolvimento de Plataforma Universal do Windows do Instalador do Visual Studio](../xaml-tools/media/uwp-workload.png)

- Para criar aplicativos no Xamarin.Forms, instale a carga de trabalho **Desenvolvimento mobile com .NET** no Visual Studio. O Blend para Visual Studio *não* será instalado, pois não dá suporte a aplicativos Xamarin.Forms.

     ![Captura de tela do desenvolvimento móvel com carga de trabalho do .NET do Instalador do Visual Studio](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Funcionalidades compartilhadas

Para tarefas de desenvolvimento mais básicas, o Visual Studio e o Blend para Visual Studio compartilham o mesmo conjunto de janelas e funcionalidades, com algumas diferenças sutis. Alguns dos destaques incluem:

- **IntelliSense:** Ambos os IDEs dão suporte a recursos do IntelliSense, como a conclusão da instrução.

- **Depuração:** Você pode depurar no [Visual Studio](inspect-xaml-properties-while-debugging.md) e [Blend para Visual Studio](../xaml-tools/debug-xaml-in-blend.md), incluindo a definição de pontos de interrupção no código para depurar um aplicativo em execução e usar a [recarga a quente](../xaml-tools/xaml-hot-reload.md) para alterar o código XAML enquanto o aplicativo está em execução. Para manter uma experiência de depuração consistente com o Visual Studio, o Blend for Visual Studio inclui a maioria das janelas de depuração e barras de ferramentas do Visual Studio.

- **Recarregamento de arquivo:** Você pode editar os arquivos XAML no Visual Studio ou Blend para Visual Studio. Os arquivos editados que foram salvos são recarregados automaticamente conforme você alterna entre os IDEs. Você pode controlar o comportamento de recarregamento navegando até **ferramentas**  >  **Opções**  >    >  **documentos** de ambiente em qualquer IDE.

- **Configurações e layouts sincronizados:** Os layouts de janela da ferramenta de personalização de design e as preferências de configurações para o Visual Studio ou Blend para Visual Studio são sincronizadas em seus dispositivos e versões quando você entra com a mesma conta de personalização. Confira [Sincronizar configurações em vários computadores](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Funcionalidades avançadas do Blend para Visual Studio

Para aumentar sua produtividade, considere o uso do Blend for Visual Studio para as tarefas a seguir. Estas são as áreas em que o Blend for Visual Studio dá mais funcionalidades do que o designer do Visual Studio ou o código isolado.

| Tarefa | Visual Studio | Blend for Visual Studio | Mais informações |
| - | - | - | - |
| **Projetar estados visuais** | Não há ferramenta para ajudar você a criar estados visuais; é necessário criá-los programaticamente. | Use ferramentas de design para alterar a aparência de um controle com base em seu estado. | [Estados visuais](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Criar animações** |Não há nenhuma ferramenta de design para animações; você precisa criá-las de forma programática. Isso exige noções básicas da animação e do sistema de tempo no WPF, além de amplas competências em codificação.|Você cria animações visualmente e pode visualizá-las no Blend for Visual Studio. Isso é mais rápido e mais preciso do que criar as animações em código. É possível adicionar gatilhos para manipular a interação do usuário e mudar para o código para adicionar manipuladores de eventos e outras funcionalidades.|[Animar objetos](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Transformar formas e texto em demarcadores para facilitar a manipulação**|Não há suporte.|Você pode fazer alterações sutis ou drásticas em formas (como retângulos e elipses) convertendo-as em demarcadores, que fornecem um melhor controle de edição. É possível alterar a forma ou combinar demarcadores, além de criar demarcadores compostos com base em várias formas.<br /><br />Você também pode converter blocos de texto em demarcadores para manipulá-los como imagens vetoriais.|[Desenhe as formas e demarcadores](../xaml-tools/draw-shapes-and-paths.md)|
|**Editar controles, modelos e estilos**|Exige a codificação e o conhecimento de estilos e modelos do WPF.|Transforme qualquer imagem em um controle.<br /><br />Use as ferramentas de edição de modelo para fazer alterações em controles, estilos e modelos com apenas alguns cliques do mouse.<br /><br />Por exemplo, é possível usar os recursos de estilo do Blend for Visual Studio para implementar controles WPF comuns (como botões, caixas de listagem, barras de rolagem, menus, etc.) e alterar a cor, o estilo ou o modelo subjacente diretamente no Blend for Visual Studio. Você pode mudar para o código para dar os toques finais, se desejar.|[Modificar o estilo de objetos](modify-the-style-of-objects-in-blend.md)|
|**Conectar a interface do usuário aos dados**|É possível criar uma fonte de dados com base em recursos, como bancos de dados SQL Server, WCF ou serviços Web, objetos ou lista do SharePoint, depois associar a fonte de dados aos controles da interface do usuário.<br /><br />Dados de tempo de design devem ser criados manualmente para proporcionar uma experiência de design interativa.|Para aplicativos do .NET Framework, crie dados de amostra com facilidade para executar protótipos e testes. Mude para dados dinâmicos quando você estiver pronto.<br /><br />As funcionalidades de geração de dados do Blend para Visual Studio são impressionantes (é possível adicionar nomes, números, URLs e fotos de maneira fácil e imediata) e podem economizar um bom tempo.<br /><br />Para dados dinâmicos, é possível associar os controles da interface do usuário a um arquivo XML ou a qualquer fonte de dados CLR.|[Exibir dados](display-data-in-blend.md)|

Para obter mais informações sobre design avançado de XAML, confira [Criar uma interface do usuário usando o Blend para Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Confira também

- [Visão geral do XAML](xaml-overview.md)
- [Visão geral do Blend para Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
