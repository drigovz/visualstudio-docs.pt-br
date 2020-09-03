---
title: Ler um modelo UML no código do programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbc55204987f4b6ea0d45c4228f6c194f1ebaf64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671306"
---
# <a name="read-a-uml-model-in-program-code"></a>Ler um modelo UML no código do programa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode carregar um modelo UML e seus diagramas usando a API UML.

## <a name="reading-a-model-in-program-code"></a><a name="Reading"></a> Lendo um modelo no código do programa
 Para acessar o conteúdo de um modelo sem mostrá-lo em uma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] janela, use `ModelingProject.LoadReadOnly()` .

 Por exemplo:

```
using Microsoft.VisualStudio.Uml.Classes;
               // for IElement
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
               // for ModelingProject
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
               // for IModelStore
...
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";
using (IModelingProjectReader projectReader =
           ModelingProject.LoadReadOnly(projectPath))
{
   IModelStore store = projectReader.Store;
   foreach (IClass umlClass in store.AllInstances<IClass>())
   {
       ...
   }
}
```

 Se você quiser ler as formas em um diagrama, deverá ler o projeto e, em seguida, o diagrama.

 Por exemplo:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
foreach (string diagramFile in projectReader. DiagramFileNames)
{
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);
  foreach (IShape<IElement> shape
         in diagram.GetChildShapes<IElement>())
  { ... }
}
```

## <a name="alternative-methods"></a>Métodos alternativos
 Para muitos aplicativos, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus permite que você referencie modelos e elementos dentro deles, com maior robustez e flexibilidade do que com os métodos descritos neste tópico. Ele fornece um método padrão para fazer links entre elementos arbitrários, seja na mesma ou em modelos diferentes. Para obter mais informações, consulte [integrar modelos UML com outros modelos e ferramentas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 Você também pode abrir modelos e diagramas na interface do usuário usando a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API. Para obter mais informações, consulte [abrir um modelo UML usando a API do Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).

## <a name="stand-alone-applications"></a><a name="Standalone"></a> Aplicativos autônomos
 O exemplo na seção anterior funcionará nas extensões do Visual Studio. É possível ler um modelo em um aplicativo autônomo, mas você deve adicionar algumas referências ao seu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projeto.

> [!NOTE]
> Os detalhes de como ler um modelo em um aplicativo autônomo provavelmente serão alterados em versões futuras do produto. Alguns recursos que podem ser acessados na versão atual podem não estar disponíveis em versões futuras.

#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Para adicionar referências para ler um modelo em um aplicativo autônomo.

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto no qual você está compilando o aplicativo e clique em **Propriedades**. No editor de propriedades, na guia **aplicativo** , defina **estrutura de destino** para a versão necessária do .NET Framework.

2. Adicione as [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] referências necessárias para acessar modelos UML, normalmente:

   - Microsoft.VisualStudio.Uml.Interfaces.dll

   - Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

3. Além das referências listadas nas seções anteriores, adicione as seguintes referências de projeto em **\Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies**:

   - Microsoft.VisualStudio.Uml.dll

   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll

     Se você quiser ler diagramas em seu aplicativo, também poderá exigir essas referências:

   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll

   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll

## <a name="see-also"></a>Consulte Também
 [Programando com a API UML](../modeling/programming-with-the-uml-api.md) [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
