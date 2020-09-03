---
title: Guia System. Activities, escolher itens da caixa de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655179"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>O guia de System.Activities, escolher a caixa de diálogo dos itens da caixa de ferramentas
Essa guia da caixa de diálogo **escolher itens de caixa de ferramentas** exibe uma lista de [!INCLUDE[wf](../includes/wf-md.md)] atividades, modelos e itens disponíveis para você. Para exibir essa lista, selecione **escolher itens da caixa de ferramentas** no menu **ferramentas** ou clicando com o botão direito do mouse na caixa de **ferramentas** e selecionando **escolher itens** para exibir os **itens escolher** lista de caixas de ferramentas e, em seguida, selecione a guia **sistema. atividades** . Na caixa, a lista contém as atividades de fluxo de trabalho dos assemblies System. Activities, System. ServiceModel. Activities e System. Activities. Core. Presentation; no entanto, somente as atividades fornecidas pelo sistema mostradas e as atividades adicionadas por meio de outros assemblies exibidos na **caixa de ferramentas** são verificadas por padrão. As atividades adicionadas recentemente são verificadas automaticamente e aparecem na caixa de **ferramentas** quando você clica em **OK** na caixa de diálogo. Além disso, esses itens aparecem na **caixa de ferramentas** em uma nova categoria que corresponde ao namespace no qual reside a atividade/item/modelo.

> [!WARNING]
> Se você tentar adicionar um conjunto que não contém quaisquer atividades de fluxo de trabalho, uma caixa de diálogo de erro é exibida para explicar que o assembly não contém quaisquer atividades.

 Essa caixa de diálogo é independente do projeto e, portanto, a guia **System. Activities** continua a aparecer em XAML autônomo ou em um tipo de projeto que não seja de fluxo de trabalho.

 A filtragem é feita em cada guia. Isso significa que não é possível adicionar atividades de fluxo de trabalho por meio da guia **componente .net** . Eles precisam ser adicionados pela própria guia **System. Activities** .

 Você pode desmarcar os itens que não deseja ver na caixa de **ferramentas** dessa guia de caixa de diálogo ou, como alternativa, pode fazer isso usando a opção de menu de contexto **excluir** na **caixa de ferramentas** e desreferenciar um assembly não remove o item da **caixa de ferramentas**.

 Criando uma instância da atividade, arrastando e soltando-os ao designer adiciona o assembly que contém o item à lista de módulos (assemblies) referenciados automaticamente. Também se a atividade referencia um assembly C 2.0, C 2.0 não adiciona à lista de assembly referenciado. O assembly C deve estar no GAC ou no mesmo diretório que a atividade B. No caso autônomo, o assembly deve estar no GAC ou nos caminhos de investigação do VS. Somente então você pode arrastar e soltar a atividade na superfície de fluxo de trabalho.

 As configurações da **caixa de ferramentas** são salvas por padrão como opções do usuário, assim, na próxima vez que você abrir a **caixa de ferramentas**, ela exibirá sua lista personalizada de atividades de fluxo de trabalho. Um efeito colateral disso é que, se você tiver adicionado seus itens de domínio específicos à caixa de **ferramentas** por meio de **escolher itens de Toolbox** , você ainda continuará vendo esses itens quando estiver trabalhando em um aplicativo de console de fluxo de trabalho também. Se você não quiser vê-los, exclua-os usando o menu de contexto ou desmarque-os na caixa de diálogo **escolher itens de caixa de ferramentas** , conforme observado anteriormente.

 As colunas nesta caixa de diálogo contém as informações a seguir:

 Nome lista os nomes das atividades de fluxo de trabalho atualmente registradas em seu computador local.

 Namespace exibe a hierarquia do .NET Framework namespace da biblioteca de classes que define a estrutura da atividade.

 Nome do assembly exibe o nome e a versão do .NET Framework assembly que contém a atividade.

 Diretório exibe o local do assembly .NET Framework que contém as atividades de fluxo de trabalho. O local padrão para todos os assemblies é o cachê global de assemblies.

 Para classificar os componentes listados, selecione todo o título de coluna.