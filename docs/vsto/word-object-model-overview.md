---
title: Visão geral do modelo de objeto do Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word object model
- Word [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Word
- objects [Office development in Visual Studio], Office object models
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71e66d6cda802b2b1243911e1927af751e2cdbe9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985387"
---
# <a name="word-object-model-overview"></a>Visão geral do modelo de objeto do Word
  Ao desenvolver soluções do Word no Visual Studio, você interage com o modelo de objeto do Word. Esse modelo de objeto consiste em classes e interfaces que são fornecidas no assembly de interoperabilidade primário para o Word e são definidas no namespace <xref:Microsoft.Office.Interop.Word>.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Este tópico fornece uma breve visão geral do modelo de objeto do Word. Para obter recursos em que você pode aprender mais sobre o modelo de objeto do Word inteiro, consulte [usar a documentação do modelo de objeto do Word](#WordOMDocumentation).

 Para obter informações sobre como usar o modelo de objeto do Word para executar tarefas específicas, consulte os seguintes tópicos:

- [Trabalhar com documentos](../vsto/working-with-documents.md)

- [Trabalhar com texto em documentos](../vsto/working-with-text-in-documents.md)

- [Trabalhar com tabelas](../vsto/working-with-tables.md)

## <a name="understanding"></a>Entender o modelo de objeto do Word
 O Word fornece centenas de objetos com os quais você pode interagir. Esses objetos são organizados em uma hierarquia que segue de maneira mais próxima a interface do usuário. Na parte superior da hierarquia está o objeto <xref:Microsoft.Office.Interop.Word.Application>. Esse objeto representa a instância atual do Word. O objeto <xref:Microsoft.Office.Interop.Word.Application> contém os objetos <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, <xref:Microsoft.Office.Interop.Word.Bookmark>e <xref:Microsoft.Office.Interop.Word.Range>. Cada um desses objetos tem muitos métodos e propriedades que você pode acessar para manipular e interagir com o objeto.

 A ilustração a seguir mostra uma exibição desses objetos na hierarquia do modelo de objeto do Word.

 ![Gráfico de modelo de objeto do Word](../vsto/media/wrwordobjectmodel.gif "Gráfico de modelo de objeto do Word")

 À primeira vista, os objetos parecem se sobrepor. Por exemplo, os objetos <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.Selection> são membros do objeto <xref:Microsoft.Office.Interop.Word.Application>, mas o objeto <xref:Microsoft.Office.Interop.Word.Document> também é um membro do objeto <xref:Microsoft.Office.Interop.Word.Selection>. Os objetos <xref:Microsoft.Office.Interop.Word.Document> e <xref:Microsoft.Office.Interop.Word.Selection> contêm objetos <xref:Microsoft.Office.Interop.Word.Bookmark> e <xref:Microsoft.Office.Interop.Word.Range>. A sobreposição existe porque há várias maneiras pelas quais você pode acessar o mesmo tipo de objeto. Por exemplo, você aplica a formatação a um objeto <xref:Microsoft.Office.Interop.Word.Range>; Mas talvez você queira acessar o intervalo da seleção atual, de um parágrafo específico, de uma seção ou de todo o documento.

 As seções a seguir descrevem brevemente os objetos de nível superior e como eles interagem entre si. Esses objetos incluem os seguintes cinco:

- Objeto de aplicativo

- Objeto Document

- Objeto de seleção

- Objeto de intervalo

- Objeto de indicador

  Além do modelo de objeto do Word, os projetos do Office no Visual Studio fornecem *itens de host* e *controles de host* que estendem alguns objetos no modelo de objeto do Word. Os itens de host e os controles de host se comportam como os objetos do Word que eles estendem, mas também têm funcionalidade adicional, como recursos de ligação de dados e eventos extras. Para obter mais informações, consulte Visão geral de [automação do Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md) e [itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

### <a name="application-object"></a>Objeto de aplicativo
 O objeto <xref:Microsoft.Office.Interop.Word.Application> representa o aplicativo Word e é o pai de todos os outros objetos. Seus membros geralmente se aplicam ao Word como um todo. Você pode usar suas propriedades e métodos para controlar o ambiente do Word.

 Em projetos de suplemento do VSTO, você pode acessar o objeto <xref:Microsoft.Office.Interop.Word.Application> usando o campo `Application` da classe `ThisAddIn`. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

 Em projetos de nível de documento, você pode acessar o objeto <xref:Microsoft.Office.Interop.Word.Application> usando a propriedade <xref:Microsoft.Office.Tools.Word.Document.Application%2A> da classe `ThisDocument`.

### <a name="document-object"></a>Objeto Document
 O objeto <xref:Microsoft.Office.Interop.Word.Document> é fundamental para programar o Word. Ele representa um documento e todo o seu conteúdo. Quando você abre um documento ou cria um novo documento, cria um novo objeto <xref:Microsoft.Office.Interop.Word.Document>, que é adicionado à coleção <xref:Microsoft.Office.Interop.Word.Documents> do objeto <xref:Microsoft.Office.Interop.Word.Application>. O documento que tem o foco é chamado de documento ativo. Ele é representado pela propriedade <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> do objeto <xref:Microsoft.Office.Interop.Word.Application>.

 As ferramentas de desenvolvimento do Office no Visual Studio estendem o objeto <xref:Microsoft.Office.Interop.Word.Document> fornecendo o tipo <xref:Microsoft.Office.Tools.Word.Document>. Esse tipo é um *item de host* que fornece acesso a todos os recursos de um objeto <xref:Microsoft.Office.Interop.Word.Document> e adiciona eventos adicionais e a capacidade de adicionar controles gerenciados.

 Ao criar um projeto de nível de documento, você pode acessar <xref:Microsoft.Office.Tools.Word.Document> membros usando a classe gerada `ThisDocument` em seu projeto. Você pode acessar membros do <xref:Microsoft.Office.Tools.Word.Document> item de host usando as palavras **-** chave or ou **this** do código na classe `ThisDocument` ou usando `Globals.ThisDocument` de código fora da classe `ThisDocument`. Para obter mais informações, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md). Por exemplo, para selecionar o primeiro parágrafo no documento, use o código a seguir.

 [!code-vb[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#120)]
 [!code-csharp[Trin_VstcoreWordAutomation#120](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#120)]

 Em projetos de suplemento do VSTO, você pode gerar <xref:Microsoft.Office.Tools.Word.Document> itens de host em tempo de execução. Você pode usar o item de host gerado para adicionar controles ao documento associado. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="selection-object"></a>Objeto de seleção
 O objeto <xref:Microsoft.Office.Interop.Word.Selection> representa a área selecionada no momento. Quando você executa uma operação na interface do usuário do Word, como texto em negrito, seleciona ou realça o texto e, em seguida, aplica a formatação. O objeto <xref:Microsoft.Office.Interop.Word.Selection> sempre está presente em um documento. Se nada estiver selecionado, ele representará o ponto de inserção. Além disso, uma seleção pode abranger vários blocos de texto que não são contíguos.

### <a name="range-object"></a>Objeto de intervalo
 O objeto <xref:Microsoft.Office.Interop.Word.Range> representa uma área contígua em um documento e é definido por uma posição de caractere inicial e uma posição de caractere final. Você não está limitado a um único objeto de <xref:Microsoft.Office.Interop.Word.Range>. Você pode definir vários objetos <xref:Microsoft.Office.Interop.Word.Range> no mesmo documento. Um objeto <xref:Microsoft.Office.Interop.Word.Range> tem as seguintes características:

- Ele pode consistir apenas no ponto de inserção, em um intervalo de texto ou no documento inteiro.

- Ele inclui caracteres não imprimíveis, como espaços, caracteres de tabulação e marcas de parágrafo.

- Pode ser a área representada pela seleção atual ou pode representar uma área diferente da seleção atual.

- Ele não é visível em um documento, ao contrário de uma seleção, que está sempre visível.

- Ele não é salvo com um documento e existe somente enquanto o código está em execução.

  Quando você insere texto no final de um intervalo, o Word expande automaticamente o intervalo para incluir o texto inserido.

### <a name="content-control-objects"></a>Objetos de controle de conteúdo
 Uma <xref:Microsoft.Office.Interop.Word.ContentControl> fornece uma maneira de controlar a entrada e a apresentação de texto e outros tipos de conteúdo em documentos do Word. Um <xref:Microsoft.Office.Interop.Word.ContentControl> pode exibir vários tipos diferentes de interface do usuário que são otimizados para uso em documentos do Word, como um controle de texto rico, um seletor de data ou uma caixa de combinação. Você também pode usar um <xref:Microsoft.Office.Interop.Word.ContentControl> para impedir que os usuários editem seções do documento ou modelo.

 O Visual Studio estende o objeto <xref:Microsoft.Office.Interop.Word.ContentControl> em vários controles de host diferentes. Enquanto o objeto <xref:Microsoft.Office.Interop.Word.ContentControl> pode exibir qualquer um dos diferentes tipos de interface do usuário que estão disponíveis para controles de conteúdo, o Visual Studio fornece um tipo diferente para cada controle de conteúdo. Por exemplo, você pode usar uma <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para criar um controle de Rich Text ou pode usar uma <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> para criar um seletor de data. Esses controles de host se comportam como o <xref:Microsoft.Office.Interop.Word.ContentControl>nativo, mas têm eventos adicionais e recursos de associação de dados. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md).

### <a name="bookmark-object"></a>Objeto de indicador
 O objeto <xref:Microsoft.Office.Interop.Word.Bookmark> representa uma área contígua em um documento, com uma posição inicial e uma posição final. Você pode usar indicadores para marcar um local em um documento ou como um contêiner para texto em um documento. Um objeto <xref:Microsoft.Office.Interop.Word.Bookmark> pode consistir no ponto de inserção ou ser tão grande quanto o documento inteiro. Uma <xref:Microsoft.Office.Interop.Word.Bookmark> tem as seguintes características que a configuram além do objeto <xref:Microsoft.Office.Interop.Word.Range>:

- Você pode nomear o indicador em tempo de design.

- <xref:Microsoft.Office.Interop.Word.Bookmark> objetos são salvos com o documento e, portanto, não são excluídos quando o código para de ser executado ou o documento é fechado.

- Os indicadores podem ser ocultados ou tornar-se visíveis definindo a propriedade <xref:Microsoft.Office.Interop.Word.View.ShowBookmarks%2A> do objeto <xref:Microsoft.Office.Interop.Word.View> como **false** ou **true**.

  O Visual Studio estende o objeto <xref:Microsoft.Office.Interop.Word.Bookmark> fornecendo o controle de host <xref:Microsoft.Office.Tools.Word.Bookmark>. O controle de host <xref:Microsoft.Office.Tools.Word.Bookmark> se comporta como um <xref:Microsoft.Office.Interop.Word.Bookmark>nativo, mas tem eventos adicionais e recursos de associação de dados. Você pode associar dados a um controle de indicador em um documento da mesma maneira que associa dados a um controle de caixa de texto em um formulário do Windows. Para obter mais informações, consulte [controle de indicadores](../vsto/bookmark-control.md).

## <a name="WordOMDocumentation"></a>Usar a documentação do modelo de objeto do Word
 Para obter informações completas sobre o modelo de objeto do Word, você pode consultar a referência do assembly de interoperabilidade primária (PIA) do Word e a referência do modelo de objeto do Visual Basic for Applications (VBA).

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A documentação de referência do PIA do Word descreve os tipos no assembly de interoperabilidade primária para o Word. Esta documentação está disponível no seguinte local: [referência de assembly de interoperabilidade primária do Word 2010](../vsto/office-primary-interop-assemblies.md).

 Para obter mais informações sobre o design do PIA do Word, como as diferenças entre classes e interfaces no PIA e como os eventos no PIA são implementados, consulte [visão geral de classes e interfaces nos assemblies de interoperabilidade primária do Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do Word conforme ele é exposto ao código do VBA. Para obter mais informações, consulte [referência de modelo de objeto do Word 2010](/office/vba/api/overview/Word/object-model).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA do Word. Por exemplo, o objeto Document na referência do modelo de objeto do VBA corresponde ao objeto <xref:Microsoft.Office.Interop.Word.Document> no PIA do Word. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência C# para Visual Basic ou Visual se quiser usá-los em um projeto do Word criado usando o Visual Studio .

## <a name="see-also"></a>Consulte também
- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)
- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Trabalhar com documentos](../vsto/working-with-documents.md)
- [Trabalhar com texto em documentos](../vsto/working-with-text-in-documents.md)
- [Trabalhar com tabelas](../vsto/working-with-tables.md)
- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
