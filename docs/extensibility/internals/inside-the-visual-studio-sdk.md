---
title: Dentro do Visual Studio SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707581"
---
# <a name="inside-the-visual-studio-sdk"></a>Por dentro do SDK do Visual Studio

Esta seção fornece informações detalhadas sobre extensões do Visual Studio, incluindo arquitetura visual studio, componentes, serviços, esquemas, utilitários e similares.

## <a name="extensibility-architecture"></a>Arquitetura de Extensibilidade
 A ilustração a seguir mostra a arquitetura de extensibilidade do Visual Studio. Os VSPackages fornecem a funcionalidade do aplicativo, que é compartilhada em todo o IDE como serviços. O IDE padrão também oferece uma ampla <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>gama de serviços, como, como, que fornecem acesso à funcionalidade de janelas DoI.

 ![Gráfico de arquitetura de ambiente](../../extensibility/internals/media/environment.gif "environment") Visão generalizada da arquitetura do Visual Studio

## <a name="vspackages"></a>VSPackages
 VSPackages são módulos de software que compõem e ampliam o Visual Studio com elementos de UI, serviços, projetos, editores e designers. VSPackages são a unidade arquitetônica central do Visual Studio. Para obter mais informações, consulte [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Shell do Visual Studio
 O visual Studio shell fornece funcionalidade básica e suporte à comunicação cruzada entre seus componentes VSPackages e extensões MEF. Para obter mais informações, consulte [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Diretrizes da Experiência do Usuário
 Se você está planejando projetar novos recursos para o Visual Studio, você deve dar uma olhada nessas diretrizes para dicas de design e usabilidade: [Visual Studio User Experience Guidelines](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Comandos
 Comandos são funções que realizam tarefas, como imprimir um documento, atualizar uma visualização ou criar um novo arquivo.

 Quando você estender o Visual Studio, você pode criar comandos e registrá-los com o shell do Visual Studio. Você pode especificar como esses comandos serão exibidos no IDE, por exemplo, em um menu ou barra de ferramentas. Normalmente, um comando personalizado aparece no menu **Ferramentas** e um comando para exibir uma janela de ferramenta apareceria no submenu **Outro Windows** do menu **Exibir.**

 Quando você cria um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando está visível ou habilitado, permite modificar seu texto e garante que o comando responda adequadamente quando ele é ativado. Na maioria dos casos, o IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lida com comandos usando a interface. Os comandos no Visual Studio são tratados a partir do contexto de comando mais interno, baseado na seleção local, e seguindo para o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal estão imediatamente disponíveis para scripting.

 Para obter mais informações, consulte [Comandos, Menus e Barras de Ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menus e barras de ferramentas
 Menus e barras de ferramentas fornecem uma maneira de os usuários invocarem comandos. Os menus são linhas ou colunas de comandos que normalmente são exibidos como itens de texto individuais na parte superior de uma janela de ferramentas. Submenus são menus secundários que aparecem quando um usuário clica em comandos que incluem uma pequena seta. Os menus de contexto aparecem quando um usuário clica com o botão direito do mouse em certos elementos de interface do usuário. Alguns nomes de menu comuns são **Arquivo,** **Edição,** **Exibição**e **Janela**. Para obter mais informações, consulte [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md).

 As barras de ferramentas são linhas ou colunas de botões e outros controles, como caixas de combinação, caixas de lista e caixas de texto. Os botões da barra de ferramentas normalmente têm imagens de ícone, como um ícone de pasta para um comando **Arquivo Aberto** ou uma impressora para um comando **Imprimir.** Todos os elementos da barra de ferramentas estão associados a comandos. Quando você clica em um botão de barra de ferramentas, seu comando associado é executado. No caso de um controle drop-down, cada item da lista de baixa está associado a um comando diferente. Alguns controles de barra de ferramentas, como um controle de divisor, são híbridos. Um lado do controle é um botão de barra de ferramentas e o outro lado é uma seta para baixo que exibe vários comandos quando é clicado.

## <a name="tool-windows"></a>Windows de ferramentas
 Janelas de ferramentas são usadas no IDE para exibir informações. **Caixa de ferramentas,** **Explorador de soluções,** janela **propriedades** e navegador **da Web** são exemplos de janelas de ferramentas.

 As janelas de ferramentas normalmente oferecem vários controles com os quais o usuário pode interagir. Por exemplo, a janela **Propriedades** permite que o usuário defina propriedades de objetos que servem a um propósito específico. A janela **Propriedades** é especializada nesse sentido, mas também geral porque pode ser usada em muitas situações diferentes. Da mesma forma, a janela **Saída** é especializada porque fornece saída baseada em texto, mas geral porque muitos subsistemas no Visual Studio podem usá-la para fornecer saída ao usuário do Visual Studio.

 Considere a seguinte imagem do Visual Studio, que contém várias janelas de ferramentas:

 ![Captura de tela](../../extensibility/internals/media/t1gui.png "T1gui")

 Algumas das janelas da ferramenta estão encaixadas em um único painel que exibe a janela da ferramenta Solution Explorer e esconde as outras janelas da ferramenta, mas as disponibiliza clicando em guias. A imagem mostra duas outras janelas de ferramentas, a **janela Lista de erros** e **saída,** encaixadas juntas em um único painel.

 Também é mostrado o painel principal de documentos, que mostra várias janelas de editor. Embora as janelas de ferramentas normalmente tenham apenas uma instância (por exemplo, você pode abrir apenas um **Solution Explorer),** as janelas do editor podem ter várias instâncias, cada uma das quais é usada para editar um documento separado, mas todas estão encaixadas no mesmo painel. A imagem mostra um painel de documentos que tem duas janelas de editor, uma janela de designer de formulário. Todas as janelas do painel de documentos estão disponíveis clicando em guias, mas a janela do editor que contém EditorPane.cs arquivo é visível e ativa.

 Quando você estende o Visual Studio, você pode criar janelas de ferramentas que permitem que os usuários do Visual Studio interajam com sua extensão. Você também pode criar seus próprios editores que permitem aos usuários do Visual Studio editar documentos. Como as janelas e editores das ferramentas serão integrados ao Visual Studio, você não precisa programá-los para acoplar ou aparecer em uma guia corretamente. Quando estiverem corretamente registrados no Visual Studio, eles terão automaticamente as características típicas das janelas de ferramentas e janelas de documentos no Visual Studio. Para obter mais informações, consulte [Estender e personalizar a ferramenta Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Janelas de documento
 Uma janela de documento é uma janela de filho emoldurada de uma janela de interface de vários documentos (MDI). Janelas de documentos normalmente são usadas para hospedar editores de texto, editores de formulários (também conhecidos como designers) ou controles de edição, mas eles também podem hospedar outros tipos funcionais. A caixa de diálogo **Arquivo Novo** inclui exemplos de janelas de documentos que o Visual Studio fornece.

 A maioria dos editores são específicos para uma linguagem de programação ou para um tipo de arquivo, como páginas HTML, conjuntos de quadros, arquivos C++ ou arquivos de cabeçalho. Ao selecionar um modelo na caixa de diálogo **Arquivo novo,** um usuário cria dinamicamente uma janela de documento para o editor para o tipo de arquivo associado ao modelo. Uma janela de documento também é criada quando um usuário abre um arquivo existente.

 As janelas de documentos são restritas à área do cliente MDI. Cada janela de documento tem uma guia na parte superior, e a ordem da guia está vinculada a outras janelas que podem estar abertas na área do MDI. Clicar com o botão direito do mouse na guia de uma janela de documento exibe um menu de atalho que inclui opções para dividir a área MDI em vários grupos de guias horizontais ou verticais. A divisão da área Desmembrada permite que vários arquivos sejam visualizados ao mesmo tempo. Para obter mais informações, consulte [Document Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editores
 O editor do Visual Studio permite personalizá-lo e usá-lo para seu próprio tipo de conteúdo por meio do Mef (Managed Extensibility Framework). Em muitos casos, você não precisará criar um VSPackage para estender o editor, embora se você quiser incluir recursos do shell (por exemplo, um comando de menu ou uma chave de atalho), você pode combinar uma extensão MEF com um VSPackage.

 Você também pode criar um editor personalizado, por exemplo, se deseja ler e escrever em um banco de dados, ou se deseja usar um designer. Você também pode usar um editor externo, como o Notepad ou o Microsoft WordPad. Para obter mais informações, consulte [Editor e Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Serviços de idiomas
 Se você quiser que o editor do Visual Studio suporte novas palavras-chave de programação ou mesmo uma nova linguagem de programação, você cria um serviço de idiomas. Cada serviço de idioma pode implementar certos recursos do editor totalmente, parcialmente ou não. Dependendo de como ele é configurado, o serviço de idiomas pode fornecer destaque de sintaxe, correspondência de chaves, suporte ao IntelliSense e outros recursos no editor.

 No coração de um serviço de linguagem estão um analisador e um scanner. Um scanner (ou lexer) divide um arquivo de origem em elementos conhecidos como tokens, e um analisador estabelece as relações entre esses tokens. Ao criar um serviço de idioma, você deve implementar o analisador e o scanner para que o Visual Studio possa entender os tokens e a gramática do idioma. Você pode criar serviços de idioma gerenciados ou não gerenciados. Para obter mais informações, consulte [Extensibility Legacy Language Service](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projetos

No Visual Studio, os projetos são os contêineres que os desenvolvedores usam para organizar e construir o código-fonte e outros recursos. Os projetos permitem que você organize, crie, depura e implante código-fonte, referências a serviços e bancos de dados da Web e outros recursos. O VSPackages pode estender o sistema de projetos do Visual Studio fornecendo tipos de projeto, subtipos de projeto e ferramentas personalizadas.

Os projetos também podem ser reunidos em uma *solução*, que é um agrupamento de um ou mais projetos que trabalham juntos para criar um aplicativo. As informações de projeto e status relativas à solução são armazenadas em dois arquivos de solução, o arquivo de solução baseada em texto [(.sinn)](solution-dot-sln-file.md) e o arquivo de opção de usuário de solução binária [(.suo).](solution-user-options-dot-suo-file.md) Esses arquivos são semelhantes aos arquivos de grupo (.vbg) que foram usados em versões anteriores do Visual Basic, e os arquivos de espaço de trabalho (.dsw) e opções de usuário (.opt) que foram usados em versões anteriores do C++.

Para obter mais informações, consulte [Projetos](../../extensibility/internals/projects.md) e [Soluções](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Modelos de item e de projeto
 O Visual Studio inclui modelos de projeto predefinidos e modelos de itens de projeto. Você também pode fazer seus próprios modelos ou adquirir modelos da comunidade e, em seguida, integrá-los ao Visual Studio. A [Galeria de Códigos MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) é o lugar para escolher modelos e extensões.

 Os modelos contêm a estrutura do projeto e os arquivos básicos necessários para construir um tipo específico de aplicativo, controle, biblioteca ou classe. Quando você quiser desenvolver um software que se assemelhe a um dos modelos, crie um projeto baseado no modelo e, em seguida, modifique os arquivos desse projeto.

> [!NOTE]
> Esta arquitetura de modelo [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] não é suportada para projetos.

 Para obter mais informações, consulte [Adicionar modelos de itens de projeto e projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Propriedades e Opções
 A janela **Propriedades** exibe as propriedades de itens únicos ou múltiplos selecionados: [Ampliando as](../../extensibility/internals/extending-properties.md) opções de propriedades as páginas contêm conjuntos de opções que pertencem a um componente específico, como uma linguagem de programação ou um VSPackage: [Páginas de Opções e Opções](../../extensibility/internals/options-and-options-pages.md). As configurações são geralmente recursos relacionados à UI que podem ser importados e exportados: [Suporte para configurações do usuário](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Serviços visuais do estúdio
 Um serviço fornece um conjunto específico de interfaces para os componentes consumirem. O Visual Studio fornece um conjunto de serviços que podem ser usados por quaisquer componentes, incluindo extensões. Por exemplo, os serviços do Visual Studio permitem que as janelas de ferramentas sejam mostradas ou ocultadas dinamicamente, habilitem o acesso a eventos de Ajuda, barra de status ou ia de usuário. O editor do Visual Studio também fornece serviços que podem ser importados por extensões de editor. Para obter mais informações, consulte [Usar e Fornecer Serviços](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Depurador
 O depurador é a interface do usuário para os componentes de depuração específicos do idioma. Se você criou um novo serviço de idioma, você precisará criar um mecanismo de depuração específico para conectar-se ao depurador. Para obter mais informações, consulte [Visual Studio Debugger Extensibility](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Controle do código-fonte
 Para obter informações sobre a implementação de um plug-in de controle de origem ou VSPackage, consulte [Source Control](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Assistentes
 Você pode criar um assistente em conjunto com um novo tipo de projeto, para que o assistente possa ajudar seus usuários a tomar as decisões certas quando criarem um novo projeto desse tipo. Para obter mais informações, consulte [Wizards](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Ferramentas personalizadas
 Ferramentas personalizadas permitem associar uma ferramenta a um item em um projeto e executar essa ferramenta sempre que o arquivo for salvo. Para obter mais informações, consulte [Ferramentas personalizadas](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilitários VSSDK
 O VSSDK inclui um conjunto de utilitários que você pode precisar para trabalhar com diferentes aspectos do VSPackages. Para obter mais informações, consulte [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Usando o Instalador do Windows
 Em alguns casos, você pode precisar usar o Instalador do Windows em vez do instalador VSIX: por exemplo, você pode precisar escrever para o registro. Para obter informações sobre como usar o Windows Installer com suas extensões, consulte [Instalar VSPackages com o Instalador do Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visualizador da Ajuda
 Você pode integrar sua própria ajuda e páginas de F1 no Visualizador de Ajuda. Para obter mais informações, consulte [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
