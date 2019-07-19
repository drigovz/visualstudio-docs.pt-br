---
title: 'Designer de fluxo de trabalho: System. Activities, escolher itens da caixa de ferramentas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd25b939519bb1a1cb179ab5bbd4d20b9307f920
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747762"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Guia de System. Activities, caixa de diálogo Escolher itens da caixa de ferramentas

Esta guia, o **Choose Toolbox Items** caixa de diálogo exibe uma lista de atividades do Windows Workflow Foundation (WF), modelos e itens disponíveis para você. Para exibir essa lista, selecione **Choose Toolbox Items** da **ferramentas** menu ou clicando com o **caixa de ferramentas** e selecionando **escolher itens**para exibir o **Choose Toolbox Items** caixa de diálogo e, em seguida, selecione sua **System. Activities** guia. Imediatamente, a lista contém atividades de fluxo de trabalho de assemblies System. Activities, Activities e Activities; No entanto, somente o sistema forneceu atividades mostradas e as atividades adicionados por meio de outros assemblies exibidos na **caixa de ferramentas** são verificadas por padrão. Adicionado recentemente atividades automaticamente são verificadas e aparecem na **caixa de ferramentas** quando você clica em **Okey** na caixa de diálogo. Além disso, esses itens aparecem na **caixa de ferramentas** em uma nova categoria que corresponde ao namespace onde o atividade/item/modelo reside.

> [!WARNING]
> Se você tentar adicionar um conjunto que não contém quaisquer atividades de fluxo de trabalho, uma caixa de diálogo de erro é exibida para explicar que o assembly não contém quaisquer atividades.

Essa caixa de diálogo é projeto desconhecido e, portanto, o **System. Activities** guia continua a aparecer em XAML de autônomo ou um tipo de projeto não fluxo de trabalho.

Filtragem é feita em cada guia, e não é possível adicionar atividades de fluxo de trabalho por meio de **componente .NET** guia. Adicioná-los por meio de **System. Activities** guia em si.

Você pode desmarcar quaisquer itens que você não deseja ver na **caixa de ferramentas** nessa caixa de diálogo guia ou como alternativa, você pode fazer isso usando o **excluir** opção de menu no botão direito do mouse a **Toolbox**e cancelando a referência de um assembly não remove o item do **caixa de ferramentas**.

Criando uma instância da atividade, arrastando e soltando-os ao designer adiciona o assembly que contém o item à lista de módulos (assemblies) referenciados automaticamente. Também se a atividade referencia um assembly C 2.0, C 2.0 não adiciona à lista de assembly referenciado. O assembly C deve estar no GAC ou no mesmo diretório que a atividade B. Em casos autônomos, o assembly deve estar no GAC ou nos caminhos de investigação do VS. Somente então você pode arrastar e soltar a atividade na superfície de fluxo de trabalho.

**Caixa de ferramentas** por padrão, as configurações são salvas como opções de usuário, portanto, a próxima vez, quando você abre o **caixa de ferramentas**, ele exibe sua lista personalizado de atividades de fluxo de trabalho. Um efeito colateral disso é que, se você tiver adicionado seus itens específicos de domínio para o **caixa de ferramentas** por meio de **Choose Toolbox Items** caixa de diálogo, você ainda continuará a consulte esses itens quando você estiver trabalhando em um Aplicativo Console do fluxo de trabalho também. Se você não deseja vê-los, excluí-los usando o menu de atalho ou desmarcá-los por meio de **Choose Toolbox Items** caixa de diálogo, conforme observado anteriormente.

As colunas nesta caixa de diálogo contém as informações a seguir:

Nome\
Lista os nomes das atividades de fluxo de trabalho registradas atualmente em seu computador local.

Namespace\
Exibe a hierarquia do namespace .NET que define a estrutura da atividade.

Nome do assembly\
Exibe o nome e versão do assembly .NET que contém a atividade.

Directory\
Exibe o local do assembly .NET que contém as atividades de fluxo de trabalho. O local padrão para todos os assemblies é o cachê global de assemblies.

Para classificar os componentes listados, selecione todo o título de coluna.