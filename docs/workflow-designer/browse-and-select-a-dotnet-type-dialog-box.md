---
title: Designer de Fluxo de Trabalho – procurar e selecionar uma caixa de diálogo de tipo .NET
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a526bc9504f4f63a7a135978ade02654bbe63ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597107"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET

Na janela **Propriedades** , caixas de diálogo ou designers como o designer de variável, quando você seleciona **procurar tipos** em uma lista de tipos de dados, é a caixa de diálogo **procurar e selecionar um tipo .net** (referenciado em uma forma abreviada como "navegador de tipo"). Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore de assemblies e de projetos.

Esta caixa de diálogo é empregada em um número de cenários do usuário, incluindo o seguinte:

- Ao definir o tipo de uma variável ou um argumento.

- Ao selecionar um tipo para uma atividade genérico.

- Para adicionar uma captura na atividade de <xref:System.Activities.Statements.TryCatch> .

> [!NOTE]
> O navegador do tipo pode exibir tipos de jagged array Visual Basic, mas não tipos de matriz multidimensional. Consulte [matrizes denteadas](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) e [matrizes multidimensionais](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) para obter detalhes.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selecionando um tipo de valor ou tipo de referência de navegador de tipo

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para selecionar um valor ou uma referência digite de navegador de tipo

1. Na caixa **nome do tipo** , digite o nome do tipo que você deseja usar.

2. Realize um dos seguintes procedimentos:

    - Depois que o nome do tipo que você deseja usar aparecer na árvore na caixa nome do **tipo** , clique duas vezes no tipo para selecioná-lo.

    - Digite caracteres suficientes na caixa **nome do tipo** para identificar exclusivamente o tipo que você deseja usar e pressione ENTER para selecionar o tipo

### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para selecionar um tipo genérico de navegador de tipo

1. Na caixa **nome do tipo** , digite o nome do tipo que você deseja usar.

2. Depois que o nome do tipo que você deseja usar aparecer na árvore na caixa nome do **tipo** , clique no tipo para selecioná-lo para fazer com que as caixas suspensas sejam exibidas.

     Selecione o tipo que você deseja usar para fechar o genérico nas caixas suspensas e clique em **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Tipos exibidos no navegador de tipo

Os tipos exibidos no navegador do tipo podem variar dependendo de como o navegador de tipo foi iniciado. Se o navegador de tipos foi iniciado a partir de um projeto de fluxo de trabalho dentro de **VS2010**, por padrão, todos os tipos nos assemblies referenciados e nos projetos referenciados são mostrados. Se o navegador de tipos tiver sido iniciado fora de um sistema de projeto **VS2010** (como em um aplicativo de fluxo de trabalho rehospedado ou em um arquivo de fluxo de trabalho autônomo), por padrão, os tipos de todos os assemblies carregados no AppDomain serão mostrados.

No navegador de tipo pode ser filtro por desenvolvedores do designer de atividade. Para quaisquer atividades determinada, você pode ver apenas um subconjunto dos tipos. Por exemplo, na atividade de <xref:System.Activities.Statements.TryCatch> , somente os tipos derivados de <xref:System.Exception> são mostrados no navegador do tipo.

## <a name="filtering-search-results-in-the-type-browser"></a>Resultados de pesquisa de filtragem no navegador de tipo

A lista de tipos na caixa **nome do tipo** fica mais curta à medida que você digita mais caracteres para encontrar uma correspondência. Somente os tipos cujo nome fullyqualified começa com a cadeia de caracteres que você digitou ou tipos cujo nome curto começa com a cadeia de caracteres digitada aparece na lista filtrada.

Por exemplo:

1. A **operação** de digitação corresponde <xref:System.OperationCanceledException> , mas não <xref:System.InvalidOperationException> . Para corresponder <xref:System.InvalidOperationException>, inicie digite System.I ou inválido.

2. Digitando correspondências **genéricas** <xref:System.GenericUriParser> , mas não tipos no <xref:System.Collections.Generic> namespace. Para procurar tipos no <xref:System.Collections.Generic> namespace, digite o nome totalmente qualificado do namespace.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selecionando um contrato de serviço usando a caixa de diálogo de navegador de tipo

Ao selecionar um tipo de contrato de serviço, o navegador do tipo mostra somente os tipos que têm o atributo de <xref:System.ServiceModel.ServiceContractAttribute> .

## <a name="see-also"></a>Confira também

- [Usando os designers de atividade](control-flow-activity-designers.md)
