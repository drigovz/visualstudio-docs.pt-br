---
title: Diretrizes para a criação de regiões de formulário do Outlook
description: Saiba mais sobre as diretrizes para criar regiões de formulário do Outlook que podem ajudá-lo a otimizar suas regiões de formulário e evitar possíveis problemas.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a3a2fab671d6302583f1207f5756118c548bd8a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933603"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Diretrizes para criar regiões de formulário do Outlook
  As informações a seguir podem ajudá-lo a otimizar suas regiões de formulário e evitar possíveis problemas:

- [Use nomes de região de formulário](#UsingFormRegions).

- [Desabilitar herança de região de formulário](#DisablingInheritance).

- [Entenda os tipos e nomes de classe de mensagem](#ClassNames).

- [Crie regiões de formulário adjacentes para o painel de leitura](#ReadingPane).

- [Use os tamanhos de ícone ideais](#UsingOptimal).

  Para obter mais informações sobre regiões de formulário, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> Usar nomes de região de formulário
 Há vários nomes usados para descrever a região do formulário. É importante entender a diferença entre esses nomes e como eles afetam a região do formulário. A tabela a seguir descreve cada nome.

|Nome da região do formulário|Descrição|
|----------------------|-----------------|
|Nome do item da região do formulário|O nome que você especifica para o item da **região de formulário do Outlook** na caixa de diálogo **Adicionar novo item** . Este é o nome do arquivo de código de região do formulário que aparece em **Gerenciador de soluções**.|
|Propriedade <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A>|Especifique esse nome no **texto descritivo de fornecimento e selecione a página preferências de exibição** do assistente de **nova região de formulário do Outlook** . Esse nome aparece como a propriedade **FormRegionName** na janela **Propriedades** .<br /><br /> Use a <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriedade para especificar o rótulo que identifica a região de formulário na interface do usuário do Outlook. Para regiões de formulário separadas, esse nome aparece como um botão na faixa de forma do item do Outlook.<br /><br /> Para regiões de formulário adjacentes, esse nome aparece como um texto de cabeçalho acima da região do formulário.|
|Atributo `Microsoft.Office.Tools.Outlook.FormRegionName`|Quando você adiciona um item de **região de formulário do Outlook** ao projeto, o Visual Studio define essa propriedade como o nome totalmente qualificado da região de formulário. O nome totalmente qualificado padrão é o nome do suplemento do VSTO conectado ao nome da região do formulário por um ponto — por exemplo, `OutlookAddIn1.FormRegion1` .<br /><br /> Esse nome totalmente qualificado também aparece como um atributo na parte superior da classe de fábrica da região de formulário.<br /><br /> Use o `Microsoft.Office.Tools.Outlook.FormRegionName` atributo para identificar exclusivamente a região do formulário em todos os suplementos do VSTO do Outlook. Você não pode alterar o valor do `Microsoft.Office.Tools.Outlook.FormRegionName` atributo renomeando o item da região do formulário ou alterando a <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> propriedade. Para alterar esse nome, você deve modificar o `Microsoft.Office.Tools.Outlook.FormRegionName` atributo no formato de arquivo de código de região.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> Desabilitar herança de região de formulário
 Por padrão, uma classe de mensagem personalizada herda todas as associações de região de formulário da classe de mensagem base. Por exemplo, uma classe de mensagem chamada `IPM.Task.Contoso` deriva de `IPM.Task` . Portanto, `IPM.Task.Contoso` o herda as associações de região de formulário de `IPM.Task` .

 Se você não quiser que a região de formulário seja associada a nenhuma classe de mensagem derivada, defina a <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propriedade da região do formulário como **true**. Por exemplo, se você associar uma região de formulário adjacente ao `IPM.Task` e definir a <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> propriedade como **true**, a região de formulário só será acrescentada à parte inferior de um formulário de tarefa padrão. A região do formulário não será acrescentada à parte inferior das versões personalizadas de um formulário de tarefa padrão.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> Entender tipos e nomes de classe de mensagem
 O nome do tipo de um item do Outlook é diferente do nome da classe de mensagem de um item do Outlook. Por exemplo, o nome do tipo de um item RSS é `Microsoft.Office.Interop.Outlook.PostItem` . O nome da classe de mensagem de um item RSS é `IPM.Post.RSS` .

 Use o nome do tipo para fazer referência a um item do Outlook no código. Para obter uma lista de nomes de tipo, consulte [associar uma região de formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

 Use o nome da classe de mensagem dos itens do Outlook no novo assistente de **região de formulário do Outlook** para associar o item à região do formulário. Para obter uma lista de nomes de classe de mensagem válidos, consulte [associar uma região de formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> Criar regiões de formulário adjacentes para o painel de leitura
 Você pode usar o painel de leitura do Outlook para visualizar um item do Outlook sem abrir o item. O painel de leitura foi projetado apenas para leitura. Portanto, os controles de entrada que você adiciona a uma região de formulário adjacente, como uma caixa de texto, podem não se comportar conforme o esperado quando o item e a região de formulário estão abertos no painel de leitura.

 Por exemplo, se um item que tem uma região de formulário adjacente estiver aberto no painel de leitura, a seguinte situação será possível:

1. Selecione algum texto em uma caixa de texto que esteja na região do formulário.

2. Pressione **excluir**.

3. O item de email inteiro é excluído em vez do texto na caixa de texto.

   Se você estiver criando uma região de formulário adjacente que contém controles de entrada, teste os controles no painel de leitura para garantir que eles funcionem corretamente. Considere adicionar um código personalizado que desabilite controles que não se comportem conforme o esperado.

   Como alternativa, você pode definir a <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> propriedade da região do formulário como **false**. Dessa forma, a região do formulário não pode ser usada no painel de leitura.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> Usar tamanhos de ícone ideais
 Você pode especificar quais ícones deseja que a região de formulário seja exibida definindo as propriedades do ícone no grupo de propriedades **ícones** da janela **Propriedades** . Use as diretrizes a seguir para obter a melhor qualidade visual:

- Para o ícone de **página** , use um arquivo PNG (Portable Network Graphics).

- Os ícones de **janela** devem ter 32 pixels por 32 pixels.

- Todos os outros ícones devem ter 16 pixels por 16 pixels.

  O ícone de **página** aparece na faixa de bits de um inspetor para itens que têm regiões de formulário separadas, substitutas ou substituídas.

  O ícone da **janela** é exibido na área de notificação e na caixa de diálogo da  + **guia** Alt para abrir itens que exibem as regiões de formulário substituição ou substituir-todas.

## <a name="see-also"></a>Confira também
- [Acessar uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Walkthrough: criar uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Associar uma região de formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
