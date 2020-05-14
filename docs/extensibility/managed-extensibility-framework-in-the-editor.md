---
title: Estrutura de extensibilidade gerenciada no Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 888c5206b87079cf9fa91cb68e9801cb3c4f8c1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702874"
---
# <a name="managed-extensibility-framework-in-the-editor"></a>Estrutura de extensibilidade gerenciada no editor
O editor é construído usando componentes MEF (Managed Extensibility Framework, estrutura de extensibilidade gerenciada). Você pode construir seus próprios componentes MEF para estender o editor, e seu código pode consumir componentes do editor também.

## <a name="overview-of-the-managed-extensibility-framework"></a>Visão geral do Quadro de Extensibilidade Gerenciada
 O MEF é uma biblioteca .NET que permite adicionar e modificar recursos de um aplicativo ou componente que segue o modelo de programação MEF. O editor do Visual Studio pode fornecer e consumir peças componentes MEF.

 O MEF está contido no conjunto .NET Framework System 4 *System.ComponentModel.Composition.dll.*

 Para obter mais informações sobre o MEF, consulte [Quadro de Extensibilidade Gerenciada (MEF).](/dotnet/framework/mef/index)

### <a name="component-parts-and-composition-containers"></a>Peças componentes e recipientes de composição
 Uma parte componente é uma classe ou um membro de uma classe que pode fazer um (ou ambos) do seguinte:

- Consumir outro componente

- Ser consumido por outro componente

  Por exemplo, considere um aplicativo de compras que tenha um componente de entrada de pedidos que depende dos dados de disponibilidade do produto fornecidos por um componente de inventário de armazém. Em termos MEF, a parte de inventário pode *exportar* dados de disponibilidade do produto, e a parte de entrada do pedido pode *importar* os dados. A parte de entrada do pedido e a parte de inventário não têm que saber um sobre o outro; o recipiente de *composição* (fornecido pela aplicação do host) é responsável pela manutenção do conjunto de exportações e pela resolução das exportações e importações.

  O recipiente <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>de composição, é tipicamente propriedade do hospedeiro. O recipiente de composição mantém um *catálogo* de peças componentes exportadas.

### <a name="export-and-import-component-parts"></a>Exportar e importar peças componentes
 Você pode exportar qualquer funcionalidade, desde que seja implementada como uma classe pública ou um membro público de uma classe (propriedade ou método). Você não precisa derivar sua <xref:System.ComponentModel.Composition.Primitives.ComposablePart>parte componente de . Em vez disso, <xref:System.ComponentModel.Composition.ExportAttribute> você deve adicionar um atributo à classe ou membro da classe que deseja exportar. Este atributo especifica o *contrato* pelo qual outra parte do componente pode importar sua funcionalidade.

### <a name="the-export-contract"></a>O contrato de exportação
 A <xref:System.ComponentModel.Composition.ExportAttribute> define a entidade (classe, interface ou estrutura) que está sendo exportada. Normalmente, o atributo de exportação leva um parâmetro que especifica o tipo de exportação.

```
[Export(typeof(ContentTypeDefinition))]
class TestContentTypeDefinition : ContentTypeDefinition {   }
```

 Por padrão, <xref:System.ComponentModel.Composition.ExportAttribute> o atributo define um contrato que é o tipo da classe exportadora.

```
[Export]
[Name("Structure")]
[Order(After = "Selection", Before = "Text")]
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }
```

 No exemplo, o `[Export]` atributo `[Export(typeof(TestAdornmentLayerDefinition))]`padrão é equivalente a .

 Você também pode exportar uma propriedade ou método, como mostrado no exemplo a seguir.

```
[Export]
[Name("Scarlet")]
[Order(After = "Selection", Before = "Text")]
public AdornmentLayerDefinition scarletLayerDefinition;
```

### <a name="import-a-mef-export"></a>Importar uma exportação MEF
 Quando você deseja consumir uma exportação MEF, você deve conhecer o contrato (tipicamente <xref:System.ComponentModel.Composition.ImportAttribute> o tipo) pelo qual foi exportado, e adicionar um atributo que tenha esse valor. Por padrão, o atributo de importação leva um parâmetro, que é o tipo da classe que ele modifica. As seguintes linhas <xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService> de código importam o tipo.

```
[Import]
internal IClassificationTypeRegistryService ClassificationRegistry;
```

## <a name="get-editor-functionality-from-a-mef-component-part"></a>Obtenha a funcionalidade do editor a partir de uma peça componente MEF
 Se o código existente for uma parte componente MEF, você pode usar metadados MEF para consumir peças componentes do editor.

#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>Para consumir a funcionalidade do editor a partir de uma peça componente MEF

1. Adicione referências ao *System.Composition.ComponentModel.dll*, que está no cache de montagem global (GAC) e às assembléias do editor.

2. Adicione as diretivas de uso relevantes.

    ```
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text;
    ```

3. Adicione `[Import]` o atributo à sua interface de serviço, da seguinte forma.

    ```
    [Import]
    ITextBufferFactoryService textBufferService;
    ```

4. Quando você tiver obtido o serviço, você pode consumir qualquer um de seus componentes.

5. Quando você tiver compilado sua montagem, coloque-a no *.. \Pasta Common7\IDE\Componentes\* da instalação do Visual Studio.

## <a name="see-also"></a>Confira também
- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
