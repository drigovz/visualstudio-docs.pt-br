---
title: Comandos, Menus e Barras de Ferramentas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709497"
---
# <a name="commands-menus-and-toolbars"></a>Comandos, menus e barras de ferramentas
Menus e barras de ferramentas são a maneira como os usuários acessam comandos em seu VSPackage. Comandos são funções que realizam tarefas, como imprimir um documento, atualizar uma visualização ou criar um novo arquivo. Menus e barras de ferramentas são maneiras gráficas convenientes de apresentar seus comandos aos usuários. Normalmente, os comandos relacionados são agrupados no mesmo menu ou barra de ferramentas.

- Os menus normalmente são exibidos como strings de uma palavra agrupadas em uma fileira na parte superior do ambiente de desenvolvimento integrado (IDE) ou uma janela de ferramenta. Os menus também podem ser exibidos como resultado de um evento com o botão direito do mouse, e são referidos como menus de atalho nesse contexto. Quando clicado, os menus se expandem para exibir um ou mais comandos. Os comandos, quando clicados, podem realizar tarefas ou iniciar submenus que contenham comandos adicionais. Alguns nomes de menu bem conhecidos são **Arquivo,** **Edição,** **Exibição**e **Janela**. Para obter mais informações, consulte [Estender menus e comandos](../../extensibility/extending-menus-and-commands.md).

- As barras de ferramentas normalmente são linhas de botões e outros controles, como caixas de combinação, caixas de lista, caixas de texto e controladores de menu. Todos os controles da barra de ferramentas estão associados a comandos. Quando você clica em um botão de barra de ferramentas, seu comando associado é ativado. Os botões da barra de ferramentas geralmente têm ícones que sugerem os comandos subjacentes, como uma impressora para um comando Imprimir. Em um controle de lista parada, cada item da lista está associado a um comando diferente. Um controlador de menu é um híbrido no qual um lado do controle é um botão de barra de ferramentas e o outro lado é uma seta para baixo que exibe comandos adicionais quando clicado. Para obter mais informações, consulte [Adicionar um controlador de menu a uma barra de ferramentas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Quando você cria um comando, você também deve criar um manipulador de eventos para ele. O manipulador de eventos determina quando o comando está visível ou habilitado, permite que você modifique seu texto e garante que o comando responda adequadamente ("rotas") quando ativado. Na maioria dos casos, o IDE <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> lida com comandos usando a interface. Os comandos em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rota de forma hierárquica, começando pelo contexto de comando mais interno, baseado na seleção local, e seguindo para o contexto mais externo, com base na seleção global. Os comandos adicionados ao menu principal estão imediatamente disponíveis para scripting. Para obter mais informações, consulte [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) e [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md).

  Para definir novos menus e barras de ferramentas, você deve descrevê-los em uma tabela de comando do Visual Studio *(.vsct).* O modelo de pacote do Visual Studio cria este arquivo para você, juntamente com os elementos necessários para suportar quaisquer comandos, barras de ferramentas e editores selecionados no modelo. Alternativamente, você pode escrever seu próprio arquivo *.vsct,* usando o esquema XML descrito aqui: [referência de esquema VSCT XML](../../extensibility/vsct-xml-schema-reference.md).

  Para obter mais informações sobre como trabalhar com arquivos *.vsct,* consulte [arquivos da tabela de comando do Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

  Os tópicos nesta seção explicam como os comandos, menus e barras de ferramentas funcionam em VSPackages.

## <a name="in-this-section"></a>Nesta seção
- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Uma descrição detalhada da especificação do formato da tabela de comando.

- [Arquivos da tabela de comando do Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Descreve uma sintaxe e compilador baseados em XML para tabelas de comando.

- [Colocação padrão de comando, grupo e barra de ferramentas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Descreve comandos predefinidos, grupos, menus e barras de ferramentas.

- [Comandos, menus e grupos definidos pelo IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Especifica os menus, comandos e grupos de comando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] predefinidos disponíveis para uso pelo IDE.

- [Design de comando](../../extensibility/internals/command-design.md)

 Explica como projetar comandos.

- [Otimizar comandos de menu e barra de ferramentas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Dá diretrizes para comandos.

- [Disponibilize comandos](../../extensibility/internals/making-commands-available.md)

 Explica como disponibilizar comandos para o Visual Studio.

- [Comandos e menus que usam conjuntos interop](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Explica como implementar comandos que usam conjuntos interop.

## <a name="related-sections"></a>Seções relacionadas
- [Roteamento de comando em VSPacotes](../../extensibility/internals/command-routing-in-vspackages.md)

 Explica o roteamento de comando em VSPackages.
