---
title: Visão geral do modelo de objeto do Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88695511d22e38262dc969d66e469441c9c3ac47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985477"
---
# <a name="visio-object-model-overview"></a>Visão geral do modelo de objeto do Visio
  Para desenvolver soluções do Office para Microsoft Office Visio, você pode interagir com o modelo de objeto do Visio. Esse modelo de objeto consiste em classes e interfaces que são fornecidas no assembly de interoperabilidade primário para o Visio e são definidas no `Microsoft.Office.Interop.Visio` namespace.

 Este tópico fornece uma breve visão geral do modelo de objeto do Visio. Para obter informações sobre como usar o modelo de objeto do Visio para executar tarefas em projetos do Office, consulte os seguintes tópicos:

- [Trabalhar com documentos do Visio](../vsto/working-with-visio-documents.md)

- [Trabalhar com formas do Visio](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Entender o modelo de objeto do Visio
 O Visio fornece muitos objetos com os quais você pode interagir. Esses objetos são organizados em uma hierarquia que segue de maneira mais próxima a interface do usuário. Na parte superior da hierarquia está o objeto [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application) . Esse objeto representa a instância atual do Visio. O `Microsoft.Office.Interop.Visio.Application` objeto contém os `Microsoft.Office.Interop.Visio.Document` objetos e, `Microsoft.Office.Interop.Visio.Page` bem como as `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` coleções e. Cada um desses objetos e coleções tem muitos métodos e propriedades que você pode acessar para manipular e interagir com ele.

 Para obter mais informações, consulte a documentação de referência do VBA para [Microsoft. Office. Interop. Visio. Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)e [Microsoft. Office. Interop. Visio. Page](/office/vba/api/Visio.Page) objects e também as coleções [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) e [Microsoft. Office. Interop. Visio. Pages](/office/vba/api/Visio.Pages) .

 As seções a seguir descrevem brevemente os objetos de nível superior e como eles interagem entre si. Esses objetos incluem os seguintes objetos:

- Objeto de aplicativo

- Objeto Document

- Objeto Page

### <a name="application-object"></a>Objeto de aplicativo
 O objeto Microsoft. Office. Interop. Visio. Application representa o aplicativo Visio e é o pai de todos os outros objetos. Seus membros geralmente se aplicam ao Visio como um todo. Você pode usar as propriedades e os métodos do Microsoft. Office. Interop. Visio. Application e dos `Microsoft.Office.Interop.Visio.ApplicationSettings` objetos para controlar o ambiente do Visio.

 Em projetos de suplemento do VSTO, você pode acessar o objeto Microsoft. Office. Interop. Visio. Application usando o `Application` campo da `ThisAddIn` classe. Para obter mais informações, consulte [Programando a validação](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Objeto Document
 O objeto Microsoft.Office.Interop.Visio.Document é fundamental para programar o Visio. Ele representa um arquivo de desenho, estêncil ou modelo. Quando você abre um documento do Visio ou cria um novo documento, cria um novo objeto Microsoft.Office.Interop.Visio.Document, que é adicionado à coleção Microsoft.Office.Interop.Visio.Documents do objeto Microsoft. Office. Interop. Visio. Application.

 O documento que tem o foco é chamado de documento ativo. Ele é representado pela `Microsoft.Office.Interop.Visio.Application.ActiveDocument` Propriedade do objeto Microsoft. Office. Interop. Visio. Application.

### <a name="page-object"></a>Objeto Page
 O objeto Microsoft. Office. Interop. Visio. Page representa a área de desenho de uma página de primeiro plano ou uma página de fundo. Você pode usar a `Microsoft.Office.Interop.Visio.Page.Background` propriedade para determinar se uma página é uma página de primeiro plano ou de plano de fundo.

 Para criar formas, você pode usar métodos que incluem os `Microsoft.Office.Interop.Visio.Page.DrawSpline` `Microsoft.Office.Interop.Visio.Page.DrawOval` métodos e. Além disso, você pode recuperar mestres de estênceis e posicionar as formas em uma página usando os `Microsoft.Office.Interop.Visio.Page.Drop` `Microsoft.Office.Interop.Visio.Page.DropMany` métodos ou.

## <a name="use-the-visio-object-model-documentation"></a>Usar a documentação do modelo de objeto do Visio
 Para obter informações completas sobre o modelo de objeto do Visio, você pode consultar a referência de modelo de objeto VBA do Visio. A referência do modelo de objeto do VBA documenta o modelo de objeto do Visio como ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Visio](/office/vba/api/overview/visio/object-model).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA (assembly de interoperabilidade principal) do Visio. Por exemplo, o `Document` objeto na referência de modelo de objeto do VBA corresponde ao tipo de Microsoft.Office.Interop.Visio.Document no pia do Visio. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência para Visual Basic ou Visual C# se quiser usá-los em um projeto de suplemento do VSTO do Visio que você cria usando o Visual Studio.

> [!NOTE]
> Neste momento, não há documentação de referência para o assembly de interoperabilidade primário do Visio.

 Para obter exemplos de código relacionados e ferramentas adicionais para criar soluções do Visio, consulte [visio 2010 Software Development Kit](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Tipos adicionais em assemblies de interoperabilidade primários
 Você pode encontrar tipos nos assemblies de interoperabilidade primária que não são visíveis para o VBA devido a diferenças de implementação. O VBA fornece uma exibição do modelo de objeto do Visio que inclui somente os objetos e membros que você pode usar diretamente. Os assemblies de interoperabilidade primários expõem o mesmo modelo de objeto, mas também incluem outras interfaces, classes e membros que convertem objetos no modelo de objeto COM em código gerenciado. Esses itens adicionais não devem ser usados diretamente no seu código.

 Para obter mais informações, consulte [visão geral de classes e interfaces nos assemblies de interoperabilidade primária do Office](/previous-versions/office/office-12/ms247299(v=office.12)) e assemblies de [interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Confira também
- [Soluções do Visio](../vsto/visio-solutions.md)
- [Trabalhar com documentos do Visio](../vsto/working-with-visio-documents.md)
- [Trabalhar com formas do Visio](../vsto/working-with-visio-shapes.md)
