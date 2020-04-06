---
title: Design de Comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709656"
---
# <a name="command-design"></a>Design de comando
Quando você adiciona um comando a um VSPackage, você deve especificar onde ele deve aparecer, quando ele está disponível e como ele deve ser tratado.

## <a name="define-commands"></a>Definir comandos
 Para definir novos comandos, inclua um arquivo de tabela de comandos Visual Studio *(.vsct)* em seu projeto VSPackage. Se você criou um VSPackage usando o modelo de pacote do Visual Studio, o projeto inclui um desses arquivos. Para obter mais informações, consulte [arquivos da tabela de comando visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 O Visual Studio mescla todos os arquivos *.vsct* que encontra para que ele possa exibir os comandos. Como esses arquivos são diferentes do binário VSPackage, o Visual Studio não precisa carregar o pacote para encontrar os comandos. Para obter mais informações, consulte [Como os VSPackages adicionam elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 O Visual <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> Studio usa o atributo de registro para definir os recursos e comandos do menu. Para obter mais informações, consulte [implementação do Comando](../../extensibility/internals/command-implementation.md).

 Os comandos podem ser alterados em tempo de execução de várias maneiras diferentes. Eles podem ser exibidos ou escondidos, habilitados ou desativados. Eles podem exibir textos ou ícones diferentes ou conter valores diferentes. Uma grande quantidade de personalização pode ser realizada antes do Visual Studio carregar seu VSPackage. Para obter mais informações, consulte [Como os VSPackages adicionam elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Manipuladores de comando
 Quando você cria um comando, você deve fornecer um manipulador de eventos para executar o comando. Se o usuário selecionar o comando, ele deve ser roteado adequadamente. Roteamento de um comando significa enviá-lo para o VSPackage correto para habilitá-lo ou desativá-lo, escondê-lo ou exibi-lo e executá-lo se o usuário optar por fazê-lo. Para obter mais informações, consulte [algoritmo de roteamento de comando](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Ambiente de comando do Visual Studio
 O Visual Studio pode hospedar qualquer número de VSPackages, e cada um pode contribuir com seu próprio conjunto de comandos. O ambiente exibe apenas os comandos apropriados à tarefa atual. Para obter mais informações, consulte os objetos [de contexto de disponibilidade](../../extensibility/internals/command-availability.md) de comando e [seleção](../../extensibility/internals/selection-context-objects.md).

 Um VSPackage que define novos comandos, menus, barras de ferramentas ou menus de atalho fornece suas informações de comando ao Visual Studio no momento da instalação por meio de entradas de registro que fazem referência a recursos em conjuntos nativos ou gerenciados. Cada recurso então faz referência a um arquivo binário de recursos de dados *(.cto),* que é produzido quando você compila um arquivo de tabela de comando visual studio *(.vsct).* Isso permite que o Visual Studio forneça conjuntos de comandos, menus e barras de ferramentas mescladas sem ter que carregar todos os VSPackage instalados.

### <a name="command-organization"></a>Organização de comando
 O ambiente posiciona comandos por grupo, prioridade e menu.

- Os grupos são coleções lógicas de comandos relacionados, por exemplo, o grupo de comando **Cortar,** **Copiar**e **Colar.** Grupos são os comandos que aparecem nos menus.

- A prioridade determina a ordem em que os comandos individuais em um grupo aparecem no menu.

- Os menus atuam como recipientes para grupos.

  O ambiente predefine alguns comandos, grupos e menus. Para obter mais informações, consulte [O comando Padrão, o grupo e a colocação da barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Um comando pode ser atribuído a um grupo primário. O grupo principal controla a posição do comando na estrutura principal do menu e na caixa de diálogo **Personalizar.** Um comando pode aparecer em vários grupos; por exemplo, um comando pode estar no menu principal, em um menu de atalho e em uma barra de ferramentas. Para obter mais informações, consulte [Como os VSPackages adicionam elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Roteamento de comando
 O processo de invocação e roteamento de comandos para VSPackages difere do processo de métodos de chamada em instâncias de objeto.

 As rotas ambientais comandam sequencialmente desde o contexto de comando mais interno (local), que se baseia na seleção atual, até o contexto mais externo (global). O primeiro contexto capaz de executar o comando é o que o manuseia. Para obter mais informações, consulte [algoritmo de roteamento de comando](../../extensibility/internals/command-routing-algorithm.md).

 Na maioria dos casos, o ambiente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lida com comandos usando a interface. Como o esquema de roteamento de comandos permite que muitos objetos diferentes lidem com comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pode ser implementado por qualquer número de objetos; estes incluem controles Do Microsoft ActiveX, implementações de visualização de janelas, objetos de documento, hierarquias de projetos e objetos VSPackage (para comandos globais). Em alguns casos especializados, por exemplo, comandos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> de roteamento em uma hierarquia, a interface deve ser implementada.

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Implementação de comando](../../extensibility/internals/command-implementation.md)|Descreve como implementar comandos em um VSPackage.|
|[Disponibilidade de comando](../../extensibility/internals/command-availability.md)|Descreve como o contexto do Visual Studio determina quais comandos estão disponíveis.|
|[Algoritmo de roteamento de comando](../../extensibility/internals/command-routing-algorithm.md)|Descreve como a arquitetura de roteamento de comandos do Visual Studio permite que os comandos sejam manipulados por diferentes VSPackages.|
|[Diretrizes de posicionamento de comando](../../extensibility/internals/command-placement-guidelines.md)|Sugere como posicionar comandos no ambiente do Visual Studio.|
|[Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Descreve como o VSPackages pode utilizar melhor a arquitetura de comando do Visual Studio.|
|[Colocação padrão de comando, grupo e barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Descreve como o VSPackages pode usar melhor os comandos incluídos no Visual Studio.|
|[Gerenciar VSPackages](../../extensibility/managing-vspackages.md)|Descreve como o Visual Studio carrega VSPackages.|
|[Arquivos da tabela de comando do Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornece informações sobre arquivos *.vsct* baseados em XML, que são usados para descrever o layout e a aparência dos comandos em VSPackages.|
