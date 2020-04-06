---
title: Padrões de interação para o Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698369"
---
# <a name="interaction-patterns-for-visual-studio"></a>Padrões de interação para Visual Studio
## <a name="overview"></a>Visão geral
 Um padrão de design, em geral, é o núcleo de um projeto que pode ser aplicado em situações específicas para resolver problemas com conjuntos semelhantes de restrições. Os projetistas de recursos e sistemas usam esses padrões de design como pontos de partida, que podem ser adaptados à sua situação específica.

 O Visual Studio possui uma biblioteca de padrões de interação comuns que devem ser considerados na construção de novos recursos. Existem dois contextos principais para nossos padrões de design: Visual Studio Client (devenv) e Visual Studio Online. Para alguns problemas de design, há um padrão onipresente que funciona bem em todas as situações. Em muitos casos, no entanto, a solução pode ser diferente para a interface do usuário que está sendo apresentada dentro de um navegador e aquela que está hospedada em um aplicativo cliente.

### <a name="visual-studio-client-pattern-types"></a>Tipos de padrão do Visual Studio Client

|Tipo de padrão|Descrição|Exemplos|
|------------------|-----------------|--------------|
|**Padrões de nível de aplicação**|Padrões de alto nível comuns ao aplicativo, determinando ou exibindo o contexto do aplicativo e contendo padrões compostos e de controle dentro deles|- Janelas de ferramentas<br />- Janelas de documentos|
|**Padrões compostos**|Padrões comuns que podem se estender através de padrões de aplicativos, ou um padrão reconhecido composto por vários controles em uma configuração distinta|- Ver comutação<br />- Construtores de listas<br />- Exibição de dados<br />- Notificações<br />- Validação<br />- Modelos de seleção|
|**Padrões de controle**|Especificidades sobre como os controles de baixo nível devem se comportar|- Vista de árvores<br />- Edição dentro de um controle de grade|

## <a name="application-patterns"></a>Padrões de aplicativo
 Em um alto nível, a interface do Visual Studio compreende várias janelas, diálogos, comandos e barras de ferramentas dentro de um único IDE. A hierarquia do Visual Studio determina o contexto e impulsiona menus. Os principais pontos de integração na interface do usuário do IDE são janelas de documentos, janelas de ferramentas, projetos, estrutura de comando, editor de texto, caixa de ferramentas, janela Propriedades e Opções de ferramentas >.

 Existem padrões básicos de uso para cada um dos principais pontos de integração na interface do usuário do IDE:

- [Menus e comandos para Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Padrões de aplicativo para Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interações de janela](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Janelas da ferramenta](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenções de editores de documentos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Diálogos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Projetos](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Padrões comuns de controle
 Os padrões de controle são principalmente sobre como os controles individuais devem se comportar. Esta é uma área em que a consistência é mais crítica.

 Os controles mais comuns no Visual Studio devem seguir as diretrizes do Desktop Windows. Nossas diretrizes incluem apenas áreas em que precisamos aumentar convenções comuns com interações específicas do Visual Studio, ou lugares em que substituímos as diretrizes inteiramente a fim de adaptar o Visual Studio para atender às necessidades de nossos usuários sofisticados.

- [Padrões de controle comuns para Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controles comuns](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controles de texto](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Botões e hiperlinks](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Padrões compostos
 Há uma série de maneiras que os usuários esperam realizar tarefas. Sempre que possível, os recursos devem ser projetados para usar esses padrões tanto para interação quanto para design visual.

 Embora existam muitos padrões compostos dentro do Visual Studio, alguns dos mais importantes no que diz respeito à consistência são:

- [Padrões de composição para Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [UI on-object e espiando](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelos de seleção](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Configurações de persistência e salvamento](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Entrada de toque](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
