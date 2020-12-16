---
title: Controle XMLNode
description: Saiba que o controle XMLNode é um objeto de nó XML mapeado que expõe eventos e pode ser associado a dados.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 58f9c5db883f55c00236bc202797dcf2ec3003f6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528338"
---
# <a name="xmlnode-control"></a>Controle XMLNode
  **Importante** As informações definidas neste tópico sobre o Microsoft Word são apresentadas exclusivamente para o benefício e o uso de indivíduos e organizações que estão localizados fora do Estados Unidos e de seus territórios ou que estão usando ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removeu uma implementação de funcionalidades específicas relacionadas ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word podem não ser lidas ou usadas por indivíduos ou organizações na Estados Unidos ou em seus territórios que estão usando ou desenvolvendo programas que são executados no, produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010; esses produtos não se comportarão da mesma forma que os produtos licenciados antes dessa data ou comprados e licenciados para uso fora do Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 O <xref:Microsoft.Office.Tools.Word.XMLNode> controle é um objeto de nó XML mapeado que expõe eventos e pode ser associado a dados. O <xref:Microsoft.Office.Tools.Word.XMLNode> controle é criado somente quando um elemento de esquema não repetitivo é mapeado para um Microsoft Office documento do Word. Depois que o Visual Studio cria o nó XML, você pode programá-lo diretamente sem ter que atravessar o modelo de objeto do Word.

 O <xref:Microsoft.Office.Tools.Word.XMLNode> controle só pode ser excluído com a remoção do mapeamento de elemento no Word.

## <a name="bind-data-to-the-control"></a>Associar dados ao controle
 Um <xref:Microsoft.Office.Tools.Word.XMLNode> controle dá suporte à vinculação de dados simples. O nó XML deve ser associado a uma fonte de dados usando a <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> propriedade. Se os dados no DataSet associado forem atualizados, o <xref:Microsoft.Office.Tools.Word.XMLNode> controle refletirá as alterações.

## <a name="formatting"></a>Formatação
 A formatação que pode ser aplicada a um <xref:Microsoft.Office.Interop.Word.XMLNode> objeto pode ser aplicada a um <xref:Microsoft.Office.Tools.Word.XMLNode> controle. Isso inclui fontes, estilos de sublinhado e estilos de caractere.

## <a name="events"></a>Eventos
 Os eventos a seguir estão disponíveis para o <xref:Microsoft.Office.Tools.Word.XMLNode> controle:

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>Comparar eventos
 Você pode capturar um evento quando o usuário move seu cursor para dentro do contexto de um controle específico <xref:Microsoft.Office.Tools.Word.XMLNode> . Por exemplo, você pode ter um <xref:Microsoft.Office.Tools.Word.XMLNode> controle chamado `Customer` que tem um <xref:Microsoft.Office.Tools.Word.XMLNode> controle filho chamado e `Company` `Company` tem dois controles filho <xref:Microsoft.Office.Tools.Word.XMLNode> chamados `CompanyName` e `CompanyRegion` da seguinte maneira:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se você quiser mostrar um controle no painel ações sempre que o cursor for movido para o `Company` nó, não deverá importar se o cursor está posicionado `CompanyName` ou `CompanyRegion` porque ambos estão dentro do contexto de `Company` . Nesse caso, você pode escrever seu código no <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento de `Company` .

 Na maioria dos casos, quando o cursor entra <xref:Microsoft.Office.Tools.Word.XMLNode> em um controle, <xref:Microsoft.Office.Tools.Word.XMLNode.Select> os <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> eventos e são gerados. A tabela a seguir mostra as diferenças entre esses eventos.

|Selecionar evento|Evento ContextEnter|
|------------------|------------------------|
|Ocorre quando o cursor é colocado dentro de um <xref:Microsoft.Office.Tools.Word.XMLNode> .|Ocorre quando o cursor é colocado dentro de um <xref:Microsoft.Office.Tools.Word.XMLNode> ou um de seus nós descendentes, de uma área fora do contexto do nó. Em outras palavras, ele é gerado somente quando o contexto é alterado.|

 Por exemplo, quando você move o cursor de fora do `Customer` para `CompanyName` o, o <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento para `Customer` , `Company` e `CompanyName` é gerado. Se você mover o cursor de `CompanyName` para `CompanyRegion` , somente o <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> evento para `CompanyRegion` será gerado porque você ainda está dentro do contexto de `Company` e `Customer` .

 Existem as mesmas diferenças entre o <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> evento e o evento <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> .

## <a name="see-also"></a>Veja também
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Controle de XMLNodes](../vsto/xmlnodes-control.md)
- [Como: adicionar controles XMLNode a documentos do Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [Como Mapear esquemas para documentos do Word dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
