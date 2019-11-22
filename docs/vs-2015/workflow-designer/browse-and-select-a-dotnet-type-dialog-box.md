---
title: Caixa de diálogo Procurar e selecionar um tipo .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297615"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>Procurar e selecione uma caixa de diálogo de tipo do .NET
Na janela **Propriedades** , caixas de diálogo ou designers, como o designer de variável, quando você seleciona **procurar tipos...** de uma lista de tipos de dados, é a caixa de diálogo **procurar e selecionar um tipo .net** (referenciada em um formulário abreviado como "navegador de tipo"). Na caixa de diálogo, você pode escolher um tipo de um modo de exibição de árvore de assemblies e de projetos.

 Esta caixa de diálogo é empregada em um número de cenários do usuário, incluindo o seguinte:

- Ao definir o tipo de uma variável ou um argumento.

- Ao selecionar um tipo para uma atividade genérico.

- Para adicionar uma captura na atividade de <xref:System.Activities.Statements.TryCatch> .

> [!NOTE]
> O navegador do tipo pode exibir tipos de jagged array Visual Basic, mas não tipos de matriz multidimensional. Consulte [matrizes denteadas](https://go.microsoft.com/fwlink/?LinkId=195226) e [matrizes multidimensionais](https://go.microsoft.com/fwlink/?LinkId=195227) para obter detalhes.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>Selecionando um tipo de valor ou tipo de referência de navegador de tipo

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>Para selecionar um valor ou uma referência digite de navegador de tipo

1. Na caixa de **Nome de Tipo** , digite o nome do tipo que você deseja usar.

2. Realize um dos seguintes procedimentos:

    - Uma vez que o nome do tipo que você deseja usar aparece na árvore na caixa de **Nome de Tipo** , clique duas vezes no tipo para selecioná-lo.

    - O tipo suficiente caracteres na caixa de **Nome de Tipo** para identificar exclusivamente o tipo que você deseja usar e então pressione ENTER para selecionar o tipo

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>Para selecionar um tipo genérico de navegador de tipo

1. Na caixa de **Nome de Tipo** , digite o nome do tipo que você deseja usar.

2. Uma vez que o nome do tipo que você deseja usar aparece na árvore na caixa de **Nome de Tipo** , clique no tipo para selecioná-lo para causar caixas suspensas aparece.

     Selecione o tipo que você deseja usar para fechar o genérico caixas suspensas, e clique em **OK**.

## <a name="types-displayed-in-the-type-browser"></a>Tipos exibidos no navegador de tipo
 Os tipos exibidos no navegador do tipo podem variar dependendo de como o navegador de tipo foi iniciado. Se o navegador de tipo foi iniciado de um projeto de fluxo de trabalho dentro de **vs2010**, por padrão qualquer tipo em assemblies referenciados e referenciou projetos são mostrados. Se o navegador de tipo foi iniciado fora de um sistema do projeto de **vs2010** (como em um aplicativo de fluxo de trabalho rehosted ou em um arquivo autônomo de fluxo de trabalho), então os tipos de todos os assemblies carregados em Appdomain são mostradas por padrão.

 No navegador de tipo pode ser filtro por desenvolvedores do designer de atividade. Para quaisquer atividades determinada, você pode ver apenas um subconjunto dos tipos. Por exemplo, na atividade de <xref:System.Activities.Statements.TryCatch> , somente os tipos derivados de <xref:System.Exception> são mostrados no navegador do tipo.

## <a name="filtering-search-results-in-the-type-browser"></a>Resultados de pesquisa de filtragem no navegador de tipo
 A lista de tipos na caixa de **Nome de Tipo** obtém mais curto medida que você digita mais caracteres para encontrar uma correspondência. Somente tipos cujo nome totalmente qualificado começa com a cadeia de caracteres que você digitou ou tipos cujo nome curto começa com a cadeia de caracteres que você digitou aparecem na lista filtrada.

 Por exemplo:

1. Digitando correspondências **mas não**de <xref:System.OperationCanceledException>Operação<xref:System.InvalidOperationException> . Para corresponder <xref:System.InvalidOperationException>, inicie digite System.I ou inválido.

2. Digitando correspondências **de**Genérica<xref:System.GenericUriParser> mas não tipos no namespace <xref:System.Collections.Generic> . Para procurar por tipos no namespace <xref:System.Collections.Generic> , digite o nome totalmente qualificado do namespace.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>Selecionando um contrato de serviço usando a caixa de diálogo de navegador de tipo
 Ao selecionar um tipo de contrato de serviço, o navegador do tipo mostra somente os tipos que têm o atributo de <xref:System.ServiceModel.ServiceContractAttribute> .

## <a name="see-also"></a>Consulte também
 [Usando os designers de atividade](../workflow-designer/using-the-activity-designers.md)