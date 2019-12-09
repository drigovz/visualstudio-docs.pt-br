---
title: controle Indicador
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Bookmark
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, controlling
- Bookmark control, data binding
- Bookmark control, events
- Bookmark control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b8557581e93c8d2ba5a54a13c04d5de74b24f71
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255142"
---
# <a name="bookmark-control"></a>controle Indicador
  O controle <xref:Microsoft.Office.Tools.Word.Bookmark> é um indicador que tem um nome exclusivo, expõe eventos e pode ser vinculado a dados. O indicador pode ser usado como um espaço reservado para marcar um item ou local em um Microsoft Office documento do Word. O <xref:Microsoft.Office.Tools.Word.Bookmark> controle é uma combinação de um <xref:Microsoft.Office.Interop.Word.Bookmark> objeto e um <xref:Microsoft.Office.Interop.Word.Range> objeto.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Em projetos de nível de documento, você pode <xref:Microsoft.Office.Tools.Word.Bookmark> adicionar controles ao seu documento em tempo de design ou em tempo de execução. Em projetos de suplemento do VSTO, você pode adicionar <xref:Microsoft.Office.Tools.Word.Bookmark> controles a qualquer documento aberto em tempo de execução. Para obter mais informações, confira [Como: Adicione controles de indicadores a documentos](../vsto/how-to-add-bookmark-controls-to-word-documents.md)do Word.

## <a name="bind-data-to-the-control"></a>Associar dados ao controle
 Um <xref:Microsoft.Office.Tools.Word.Bookmark> controle dá suporte à vinculação de dados simples. O indicador deve ser associado a uma fonte de dados usando <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> a propriedade. A propriedade de associação de dados padrão do indicador é <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> a propriedade.

 Se os dados no DataSet associado forem atualizados, o <xref:Microsoft.Office.Tools.Word.Bookmark> controle mostrará as alterações.

 Em projetos de nível de documento, você também pode associar dados a indicadores usando a janela **fontes de dados** . Para obter mais informações, confira [Como: Preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md).

## <a name="formatting"></a>Formatação
 A formatação que pode ser aplicada a <xref:Microsoft.Office.Interop.Word.Bookmark> um pode ser aplicada a <xref:Microsoft.Office.Tools.Word.Bookmark> um controle. Essa formatação inclui fontes, recuos, espaçamento, numeração e estilos.

## <a name="assign-text-to-the-bookmark"></a>Atribuir texto ao indicador
 Uma diferença adicional entre um <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objeto e um <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> controle é como ele se comporta quando o texto é atribuído ao indicador. Se você atribuir texto a um comprimento <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType>zero, o texto será anexado à direita do indicador e o indicador permanecerá com comprimento zero. No entanto, se você atribuir texto a um comprimento <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType>zero, o texto será inserido no indicador e o comprimento do indicador se expandirá para o número total de caracteres inseridos.

 O <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> controle também tem a <xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType> propriedade. Essa propriedade é diferente da <xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType> propriedade que está disponível <xref:Microsoft.Office.Tools.Word.Bookmark.Range?displayProperty=nameWithType> na propriedade de um <xref:Microsoft.Office.Tools.Word.Bookmark?displayProperty=nameWithType> controle ou da <xref:Microsoft.Office.Interop.Word.Bookmark.Range?displayProperty=nameWithType> propriedade de um <xref:Microsoft.Office.Interop.Word.Bookmark?displayProperty=nameWithType> objeto.

|Propriedade Text|Descrição|
|-------------------|-----------------|
|<xref:Microsoft.Office.Tools.Word.Bookmark.Text?displayProperty=nameWithType>|Use essa propriedade para exibir texto dentro do indicador e deixar o indicador no documento. A atribuição de texto ao indicador expande o intervalo de indicadores e não exclui o indicador.<br /><br /> Por exemplo, `Bookmark1.Text = "Hello world"` insere o texto no indicador e deixa o indicador intacto.|
|<xref:Microsoft.Office.Interop.Word.Range.Text?displayProperty=nameWithType>|Use essa propriedade para exibir texto no local do indicador e excluir automaticamente o indicador. Por exemplo, `Bookmark1.Range.Text = "Hello world"` insere o texto no indicador e exclui o indicador.|

## <a name="rename-the-control-at-design-time"></a>Renomear o controle em tempo de design
 Em projetos de nível de documento, quando você arrasta <xref:Microsoft.Office.Tools.Word.Bookmark> um controle da **caixa de ferramentas** para o documento, o Visual Studio gera automaticamente um nome para o controle. Você pode alterar o nome do controle na janela **Propriedades** .

## <a name="overlapping-controls"></a>Sobrepondo controles
 Os controles de indicador podem se sobrepor. O mesmo texto pode ser compartilhado por mais de um indicador. Quando você atribui novo texto a um dos indicadores sobrepostos, ele contém apenas o novo texto e os indicadores não se sobrepõem mais. O outro indicador agora contém apenas o texto que não foi compartilhado entre os indicadores sobrepostos originais.

 A tabela a seguir mostra como a frase "Este é um texto de exemplo". é compartilhado por dois indicadores sobrepostos:

|Indicador|Texto|
|--------------|----------|
|Sobrepondo indicadores|[este é o texto de {Sample].}|
|Bookmark1|Este é um exemplo|
|Bookmark2|texto de exemplo.|

 Se você atribuir o novo texto "isto é substituto". para Bookmark1, os indicadores não se sobrepõem e o Bookmark2 retém apenas o texto que originalmente não fazia parte do Bookmark1.

|Indicador|Texto|
|--------------|----------|
|Dois indicadores separados|[isso é substituição] {Text.}|
|Bookmark1|Isso é substituto|
|Bookmark2|texto.|

Se você alterar o texto de um indicador que contém outro indicador, o indicador interno não será excluído. No entanto, o indicador interno se torna um indicador vazio e passa para o final do indicador externo.

A tabela a seguir mostra como a frase "Este é um texto de exemplo". é compartilhado por um indicador que está contido em outro indicador:

|Indicador|Texto|
|--------------|----------|
|Sobrepondo indicadores|[este é o texto de {Sample}.]|
|Bookmark1|Este é um texto de exemplo.|
|Bookmark2|exemplo|

 Se você atribuir o novo texto "isto é substituto". para Bookmark1, os indicadores não são mais sobrepostos e Bookmark2 se torna um indicador vazio que está localizado no final de Bookmark1.

|Indicador|Texto|
|--------------|----------|
|Dois indicadores separados|[isso é substituição.]{}|
|Bookmark1|Isso é substituto.|
|Bookmark2|*\<empty>*|

## <a name="events"></a>Eventos

Os eventos a seguir estão disponíveis para <xref:Microsoft.Office.Tools.Word.Bookmark> o controle:

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Word.Bookmark.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Deselected>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.Bookmark.Selected>

- <xref:Microsoft.Office.Tools.Word.Bookmark.SelectionChange>

## <a name="see-also"></a>Consulte também

- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Como: Adicionar controles de indicador a documentos do Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Passo a passo: Criar menus de atalho para indicadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)