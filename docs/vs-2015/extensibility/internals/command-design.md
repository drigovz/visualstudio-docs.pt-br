---
title: Design de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195071"
---
# <a name="command-design"></a>Design de comando
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando você adiciona um comando a um VSPackage, é necessário especificar onde ele deve aparecer, quando ele está disponível e como ele deve ser manipulado.  
  
## <a name="defining-commands"></a>Definindo comandos  
 Para definir novos comandos, inclua um arquivo de tabela de comando (. vsct) do Visual Studio em seu projeto do VSPackage. Se você tiver criado um VSPackage usando o modelo de pacote do Visual Studio, o projeto incluirá um desses arquivos. Para obter mais informações, consulte [tabela de comandos do Visual Studio (. Vsct) arquivos](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 O Visual Studio mescla todos os arquivos. vsct encontrados para que ele possa exibir os comandos. Como esses arquivos são diferentes do binário VSPackage, o Visual Studio não precisa carregar o pacote para localizar os comandos. Para obter mais informações, consulte [como VSPackages adicionar elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 O Visual Studio usa o <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atributo de registro para definir recursos de menu e comandos. Para obter mais informações, consulte [implementação](../../extensibility/internals/command-implementation.md).  
  
 Os comandos podem ser alterados em tempo de execução de várias maneiras diferentes. Eles podem ser exibidos ou ocultos, habilitados ou desabilitados. Eles podem exibir textos ou ícones diferentes ou conter valores diferentes. Uma grande quantidade de personalização pode ser executada antes que o Visual Studio carregue seu VSPackage. Para obter mais informações, consulte [como VSPackages adicionar elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Manipuladores de comandos  
 Ao criar um comando, você deve fornecer um manipulador de eventos para executar o comando. Se o usuário selecionar o comando, ele deverá ser roteado adequadamente. O roteamento de um comando significa enviá-lo para o VSPackage correto para habilitá-lo ou desabilitá-lo, ocultá-lo ou exibi-lo, e executá-lo se o usuário optar por fazê-lo. Para obter mais informações, consulte [algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>O ambiente de comando do Visual Studio  
 O Visual Studio pode hospedar qualquer número de VSPackages, e cada um pode contribuir com seu próprio conjunto de comandos. O ambiente exibe somente os comandos que são apropriados para a tarefa atual. Para obter mais informações, consulte [disponibilidade](../../extensibility/internals/command-availability.md) e [objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md).  
  
 Um VSPackage que define novos comandos, menus, barras de ferramentas ou menus de atalho fornece suas informações de comando para o Visual Studio no momento da instalação por meio de entradas do registro que fazem referência a recursos em assemblies nativos ou gerenciados. Em seguida, cada recurso faz referência a um arquivo de recurso de dados binários (. CTO), que é produzido quando você compila um arquivo de tabela de comando (. vsct) do Visual Studio. Isso permite que o Visual Studio forneça conjuntos de comandos mesclados, menus e barras de ferramentas sem precisar carregar todos os VSPackage instalados.  
  
### <a name="command-organization"></a>Organização de comando  
 O ambiente posiciona os comandos por grupo, prioridade e menu.  
  
- Os grupos são coleções lógicas de comandos relacionados, por exemplo, o grupo de comandos **recortar**, **copiar**e **colar** . Os grupos são os comandos que aparecem nos menus.  
  
- A prioridade determina a ordem na qual os comandos individuais em um grupo aparecem no menu.  
  
- Os menus atuam como contêineres para grupos.  
  
  O ambiente predefine alguns comandos, grupos e menus. Para obter mais informações, consulte [comando padrão, grupo e posicionamento da barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
  Um comando pode ser atribuído a um grupo primário. O grupo primário controla a posição do comando na estrutura do menu principal e na caixa de diálogo **Personalizar** . Um comando pode aparecer em vários grupos; por exemplo, um comando pode estar no menu principal, em um menu de atalho e em uma barra de ferramentas. Para obter mais informações, consulte [como VSPackages adicionar elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Roteamento de comando  
 O processo de invocar e rotear comandos para VSPackages difere do processo de chamada de métodos em instâncias de objeto.  
  
 O ambiente roteia os comandos sequencialmente do contexto de comando mais interno (local), que é baseado na seleção atual, para o contexto mais externo (global). O primeiro contexto que é capaz de executar o comando é aquele que o manipula. Para obter mais informações, consulte [algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md).  
  
 Na maioria dos casos, o ambiente manipula os comandos usando a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Como o esquema de roteamento de comandos permite que muitos objetos diferentes manipulem comandos, o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pode ser implementado por qualquer número de objetos; eles incluem controles Microsoft ActiveX, implementações de exibição de janela, objetos de documento, hierarquias de projeto e objetos VSPackage propriamente ditos (para comandos globais). Em alguns casos especializados, por exemplo, os comandos de roteamento em uma hierarquia, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface deve ser implementada.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Implementação](../../extensibility/internals/command-implementation.md)|Descreve como implementar comandos em um VSPackage.|  
|[Disponibilidade](../../extensibility/internals/command-availability.md)|Descreve como o contexto do Visual Studio determina quais comandos estão disponíveis.|  
|[Algoritmo de roteamento](../../extensibility/internals/command-routing-algorithm.md)|Descreve como a arquitetura de roteamento de comandos do Visual Studio permite que os comandos sejam manipulados por diferentes VSPackages.|  
|[Diretrizes de posicionamento](../../extensibility/internals/command-placement-guidelines.md)|Sugere como posicionar comandos no ambiente do Visual Studio.|  
|[Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Descreve como o VSPackages pode utilizar melhor a arquitetura de comando do Visual Studio.|  
|[Posicionamento padrão de comando, grupo e barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Descreve como o VSPackages pode usar melhor os comandos incluídos no Visual Studio.|  
|[Gerenciar VSPackages](../../extensibility/managing-vspackages.md)|Descreve como o Visual Studio carrega o VSPackages.|  
|[Arquivos .Vsct (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Fornece informações sobre arquivos. vsct baseados em XML, que são usados para descrever o layout e a aparência de comandos no VSPackages.|
