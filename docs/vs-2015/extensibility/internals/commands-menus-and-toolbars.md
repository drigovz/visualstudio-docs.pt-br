---
title: Comandos, menus e barras de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 337bc4de9171d2f98bf0be0068b298b7f600b979
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155843"
---
# <a name="commands-menus-and-toolbars"></a>Comandos, menus e barras de ferramentas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Menus e barras de ferramentas são a maneira como os usuários acessam comandos em seu VSPackage. Os comandos são funções que realizam tarefas, como imprimir um documento, atualizar uma exibição ou criar um novo arquivo. Menus e barras de ferramentas são maneiras gráficas convenientes de apresentar seus comandos aos usuários. Normalmente, os comandos relacionados são agrupados no mesmo menu ou barra de ferramentas.  
  
- Os menus normalmente são exibidos como cadeias de caracteres de uma palavra agrupadas em uma linha na parte superior do ambiente de desenvolvimento integrado (IDE) ou de uma janela de ferramentas. Os menus também podem ser exibidos como resultado de um evento de clique com o botão direito do mouse e são chamados de menus de atalho nesse contexto. Quando clicado, os menus expandem para exibir um ou mais comandos. Os comandos, quando clicados, podem executar tarefas ou iniciar submenus que contêm comandos adicionais. Alguns nomes de menu bem conhecidos são arquivo, edição, exibição e janela. Para obter mais informações, consulte [estendendo menus e comandos](../../extensibility/extending-menus-and-commands.md).  
  
- Normalmente, as barras de ferramentas são linhas de botões e outros controles, como caixas de combinação, caixas de listagem, caixas de texto e controladores de menu. Todos os controles da barra de ferramentas estão associados a comandos. Quando você clica em um botão da barra de ferramentas, seu comando associado é ativado. Os botões da barra de ferramentas geralmente têm ícones que sugerem os comandos subjacentes, como uma impressora para um comando Print. Em um controle de lista suspensa, cada item da lista é associado a um comando diferente. Um controlador de menu é um híbrido no qual um lado do controle é um botão da barra de ferramentas e o outro lado é uma seta para baixo que exibe comandos adicionais quando clicado. Para obter mais informações, consulte [adicionando um controlador de menu a uma barra de ferramentas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
- Ao criar um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando é visível ou habilitado, permite que você modifique seu texto e garante que o comando responda adequadamente ("rotas") quando ativado. Na maioria dos casos, o IDE manipula comandos usando a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Comandos em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] rota de maneira hierárquica, começando com o contexto de comando mais interno, com base na seleção local, e prosseguindo para o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal estão imediatamente disponíveis para scripts. Para obter mais informações, consulte [MenuCommands vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) e [objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md).  
  
  Para definir novos menus e barras de ferramentas, você deve descrevê-los em um arquivo de tabela de comando do Visual Studio (. vsct). O modelo de pacote do Visual Studio cria esse arquivo para você, juntamente com os elementos necessários para dar suporte a quaisquer comandos, barras de ferramentas e editores selecionados no modelo. Como alternativa, você pode escrever seu próprio arquivo. vsct, usando o esquema XML descrito aqui: [referência de esquema XML vsct](../../extensibility/vsct-xml-schema-reference.md).  
  
  Para obter mais informações sobre como trabalhar com arquivos. vsct, consulte a [tabela de comandos do Visual Studio (. Vsct) arquivos](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
  Os tópicos nesta seção explicam como os comandos, menus e barras de ferramentas funcionam no VSPackages.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Uma descrição detalhada da especificação de formato de tabela de comando.  
  
 [Arquivos .Vsct (Visual Studio Command Table)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Descreve uma sintaxe baseada em XML e um compilador para tabelas de comando.  
  
 [Posicionamento padrão de comando, grupo e barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Descreve comandos, grupos, menus e barras de ferramentas predefinidos.  
  
 [Grupos, menus e comandos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Especifica os menus, comandos e grupos de comandos predefinidos disponíveis para uso pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Design de comando](../../extensibility/internals/command-design.md)  
 Explica como criar comandos.  
  
 [Otimizando os comandos do menu e da barra de ferramentas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Fornece diretrizes para comandos.  
  
 [Disponibilizando comandos](../../extensibility/internals/making-commands-available.md)  
 Explica como disponibilizar comandos para o Visual Studio.  
  
 [Comandos e menus que usam assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explica como implementar comandos que usam assemblies de interoperabilidade.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explica o roteamento de comandos em VSPackages.
