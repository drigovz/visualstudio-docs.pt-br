---
title: Comandos definidos pelo IDE para ampliação de sistemas de projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707733"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>Comandos definidos pelo IDE para estender sistemas de projeto
Quando você deseja estender sistemas de projeto, você pode usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comandos e grupos de comando fornecidos pelo IDE.

 As seções a seguir listam itens de comando que são especialmente úteis para estender sistemas de projeto.

## <a name="command-menus"></a>Menus de comando
 A tabela a seguir mostra os menus de comando que são locais úteis para você colocar comandos de alto nível que invocam um extensor de projeto.

|Menu de comando|Descrição|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|O menu de alto nível **do Projeto.**|
|IDM_VS_TOOL_PROJWIN|A barra de ferramentas **do Solution Explorer.**|

## <a name="shortcut-menus"></a>Menus de atalho
 A tabela a seguir mostra os menus de atalho que se aplicam quando um único nó é selecionado no **Solution Explorer**, ou quando há várias seleções homogêneas no **Solution Explorer**, que é quando todos os nós selecionados são do mesmo tipo.

|Menu de atalho|Descrição|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|Aplica-se quando o nó do projeto é selecionado.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|Aplica-se quando um arquivo é selecionado.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|Aplica-se quando uma pasta é selecionada.|
|IDM_VS_CTXT_WEBREFFOLDER|Aplica-se quando a pasta De referência da Web é selecionada.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|Aplica-se quando o nó raiz de referências chamado "Referências" é selecionado.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|Aplica-se quando os nós de referência são selecionados; estes incluem apenas referências de montagem, COM e projeto. Não inclui referências da Web.|

 A tabela a seguir mostra os menus de atalho que se aplicam quando a seleção no **Solution Explorer** abrange várias hierarquias,

|Menu de atalho|Descrição|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|Aplica-se quando a seleção atual contém os nós de solução e os nós de projeto raiz.|
|IDM_VS_CTXT_XPROJ_SLNITEM|Aplica-se quando a seleção atual contém o nó de solução e itens do projeto.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|Aplica-se quando a seleção atual consiste apenas em vários nós de projeto raiz.|
|IDM_VS_CTXT_XPROJ_PROJITEM|Aplica-se quando a seleção atual contém uma mistura de nós de projeto raiz e itens do projeto. Além disso, a seleção pode conter o nó de solução.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|Aplica-se quando a seleção atual contém itens de projeto de vários projetos na solução ou quando itens de diferentes tipos são selecionados no mesmo projeto.|

## <a name="command-groups"></a>Grupos de Comando
 A tabela a seguir mostra os grupos de comando que você pode <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> usar quando estende projetos e que você pode acessar através do menu de atalho.

|Grupo de comando|Descrição|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|Comandos para construção, reconstrução e implantação do projeto.|
|IDG_VS_CTXT_COMPILELINK|Comandos para compilar e vincular o projeto.|
|IDG_VS_CTXT_PROJECT_CONFIG|Comandos que definem a configuração do projeto e a ordem de construção.|
|IDG_VS_CTXT_PROJECT_ADD|Comandos que adicionam itens ao projeto.|
|IDG_VS_CTXT_PROJECT_START|Comandos que definem o projeto de inicialização associado à chave F5.|
|IDG_VS_CTXT_PROJECT_SAVE|Comandos para salvar itens do projeto.|
|IDG_VS_CTXT_PROJECT_DEBUG|Comandos para depuração.|
|IDG_VS_CTXT_PROJECT_SCC|Comandos para o controle de origem.|
|IDG_VS_CTXT_PROJECT_TRANSFER|Comandos para operações de corte, cópia e cola.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|Comandos que fornecem acesso à caixa de diálogo Propriedades do **Projeto.**|

## <a name="see-also"></a>Confira também

- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Criar grupos reutilizáveis de botões](../../extensibility/creating-reusable-groups-of-buttons.md)
