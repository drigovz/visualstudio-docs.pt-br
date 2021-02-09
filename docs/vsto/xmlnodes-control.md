---
title: Controle XMLNodes
description: Saiba que o controle XMLNodes é criado somente quando um elemento de esquema repetitivo é mapeado em um documento do Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d920df609c8172b6329cac537d10868e5795be12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894381"
---
# <a name="xmlnodes-control"></a>Controle XMLNodes
  **Importante** As informações definidas neste tópico sobre o Microsoft Word são apresentadas exclusivamente para o benefício e o uso de indivíduos e organizações que estão localizados fora do Estados Unidos e de seus territórios ou que estão usando ou desenvolvendo programas que são executados em produtos do Microsoft Word que foram licenciados pela Microsoft antes de janeiro de 2010, quando a Microsoft removeu uma implementação de funcionalidades específicas relacionadas ao XML personalizado do Microsoft Word. Essas informações sobre o Microsoft Word podem não ser lidas ou usadas por indivíduos ou organizações na Estados Unidos ou em seus territórios que estão usando ou desenvolvendo programas que são executados no, produtos do Microsoft Word que foram licenciados pela Microsoft após 10 de janeiro de 2010; esses produtos não se comportarão da mesma forma que os produtos licenciados antes dessa data ou comprados e licenciados para uso fora do Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle é uma coleção de objetos de nó XML mapeados que expõe eventos. O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle é criado somente quando um elemento de esquema repetitivo é mapeado para um Microsoft Office documento do Word. Se o elemento repetitivo contiver elementos filho, cada um dos elementos filho também será criado como um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle.

 Depois que o Visual Studio cria a coleção de nós XML, você pode programar no controle diretamente sem ter que atravessar o modelo de objeto do Word. O <xref:Microsoft.Office.Tools.Word.XMLNodes> controle só pode ser excluído com a remoção do mapeamento de elemento do documento.

> [!NOTE]
> Se você acessar um elemento filho do <xref:Microsoft.Office.Tools.Word.XMLNodes> controle por meio da <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> propriedade, ele retornará um <xref:Microsoft.Office.Interop.Word.XMLNode> objeto em vez de um <xref:Microsoft.Office.Tools.Word.XMLNode> controle. Para obter mais informações, consulte [limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="bind-data-to-the-control"></a>Associar dados ao controle
 Um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle não oferece suporte à vinculação de dados. Isso ocorre porque o <xref:Microsoft.Office.Tools.Word.XMLNodes> controle não tem recursos de ligação de dados complexos, e a vinculação de dados simples não pode representar dados repetidos.

## <a name="formatting"></a>Formatação
 Qualquer formatação que possa ser aplicada ao texto dentro do documento pode ser aplicada a um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle.

## <a name="events"></a>Eventos
 Os eventos disponíveis para o <xref:Microsoft.Office.Tools.Word.XMLNodes> controle são:

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>Comparar eventos
 Você pode capturar um evento quando o usuário move seu cursor para dentro do contexto de um controle específico <xref:Microsoft.Office.Tools.Word.XMLNodes> . Por exemplo, você pode ter um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle chamado `Customer` que tem um <xref:Microsoft.Office.Tools.Word.XMLNodes> controle filho chamado e `Company` `Company` tem dois controles filho <xref:Microsoft.Office.Tools.Word.XMLNodes> chamados `CompanyName` e `CompanyRegion` da seguinte maneira:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 Se você quiser mostrar um controle no painel ações sempre que o cursor for movido para o `Company` nó, não deverá importar se o cursor está posicionado `CompanyName` ou `CompanyRegion` porque ambos estão dentro do contexto de `Company` . Nesse caso, você pode escrever seu código no <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento de `Company` .

 Na maioria dos casos, quando o cursor entra <xref:Microsoft.Office.Tools.Word.XMLNodes> em um controle, <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> os <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos e são gerados. A tabela a seguir mostra as diferenças entre esses eventos.

|Selecionar evento|Evento ContextEnter|
|------------------|------------------------|
|Ocorre quando o cursor é colocado dentro de um dos nós da coleção <xref:Microsoft.Office.Tools.Word.XMLNodes>.|Ocorre quando o cursor é movido para dentro de um dos nós, ou nós descendentes, da coleção <xref:Microsoft.Office.Tools.Word.XMLNodes> para uma área fora do contexto do nó. Em outras palavras, ele é gerado somente quando o contexto é alterado e pode ser gerado para vários controles aninhados <xref:Microsoft.Office.Tools.Word.XMLNodes> .|

 Por exemplo, quando você move o cursor de fora do `Customer` para `CompanyName` o, os <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> eventos para `Customer` , `Company` e `CompanyName` são gerados. Se você mover o cursor de `CompanyName` para `CompanyRegion` , o <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> evento somente para `CompanyRegion` será gerado, pois o contexto é o mesmo para `Company` e `Customer` . Você pode ter vários `Company` nós em seu documento. Se você mover o cursor do `CompanyName` nó de um `Company` para o `CompanyName` nó de outro `Company` , o contexto será o mesmo, de modo que somente o <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> evento será gerado.

 Existem as mesmas diferenças entre o <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> evento e o <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> evento.

## <a name="see-also"></a>Confira também
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Controle XMLNode](../vsto/xmlnode-control.md)
- [Como: adicionar controles de XMLNodes a documentos do Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [Como Mapear esquemas para documentos do Word dentro do Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
