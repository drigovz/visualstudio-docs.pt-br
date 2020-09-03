---
title: Configurando uma imagem de plano de fundo em um diagrama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b7d206852101a1d99a08eac710d88e93afe4a04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671202"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Definindo uma imagem de plano de fundo em um diagrama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No SDK de Visualização e Modelagem do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], você pode configurar a imagem de plano de fundo para um designer gerado usando código personalizado.

## <a name="setting-the-background-image"></a>Configuração da imagem da tela de fundo

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Para configurar uma imagem de plano de fundo de um designer gerado

1. Copie o arquivo de imagem que você deseja usar como plano de fundo do diagrama no diretório Dsl\Resources do projeto atual.

2. Em **Gerenciador de soluções**, clique com o botão direito do mouse na pasta Dsl\Resources, aponte para **Adicionar**e clique em **Item existente**.

3. Na caixa de diálogo **Adicionar item existente** , navegue até a pasta Dsl\Resources.

4. Na lista **arquivos do tipo** , clique em **arquivos de imagem**.

5. Clique no arquivo de imagem que você copiou para o diretório e, em seguida, clique em **Adicionar**.

6. Clique com o botão direito do mouse em DSL e clique em **Propriedades** para abrir as propriedades do projeto DSL.

7. Na guia **recursos** , clique em **este projeto não contém um arquivo de recursos padrão. Clique aqui para criar um.**

8. Adicione o arquivo de imagem ao arquivo de recurso arrastando a imagem de **Gerenciador de soluções** para a janela de recursos.

9. Abra o menu Arquivo e clique na opção para salvar as propriedades do projeto.

10. Verifique se o arquivo Dsl\Properties\Resources.resx existe e se possui o arquivo Resources.Designer.cs nele.

11. Se Resources.Designer.cs estiver ausente, clique no arquivo Resources. resx em **Gerenciador de soluções**.

12. Na janela **Propriedades** , defina a `Custom Tool` propriedade como `ResXFileCodeGenerator` .

13. Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto DSL, aponte para **Adicionar**e clique em **nova pasta**.

14. Nomeie a pasta como **personalizada**.

15. Clique com o botão direito do mouse na pasta personalizada, aponte para **Adicionar**e clique em **novo item**.

16. Na caixa de diálogo **Adicionar novo item** , na lista **modelos** , clique em **arquivo de código**.

17. Na caixa **nome** , digite `BackgroundImage.cs` e clique em **Adicionar**.

18. Copie o código a seguir no arquivo BackgroundImage.cs, ajustando o namespace, o nome da classe do diagrama e o nome do recurso do arquivo de imagem.

     Substitua "MyDiagramClass" pelo nome da classe parcial do diagrama definido em Dsl\GeneratedCode\Diagrams.cs. Também é possível recuperar o namespace correto do arquivo Dsl\GeneratedCode\Diagrams.cs.

    ```
    using System;
    using Microsoft.VisualStudio.Modeling.Diagrams;

    // Fix the namespace:
    namespace Fabrikam.MyLanguage
    {
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs

      public partial class Language29Diagram
      {
        protected override void InitializeInstanceResources()
        {
          // Fix the Resources namespace and the Image resource name:
          ImageField backgroundField = new ImageField("background",
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);

          backgroundField.DefaultFocusable = false;
          backgroundField.DefaultSelectable = false;
          backgroundField.DefaultVisibility = true;
          backgroundField.DefaultUnscaled = false;

          shapeFields.Add(backgroundField);

          backgroundField.AnchoringBehavior
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);
          backgroundField.AnchoringBehavior
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);
          backgroundField.AnchoringBehavior
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);
          backgroundField.AnchoringBehavior
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);

          base.InitializeInstanceResources();
        }
      }
    }
    ```

     Para obter mais informações sobre como personalizar o modelo com o código do programa, consulte [navegando e atualizando um modelo no código do programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Consulte Também
 [Definindo formas e conectores](../modeling/defining-shapes-and-connectors.md) que [personalizam campos de texto e imagem](../modeling/customizing-text-and-image-fields.md) [navegando e atualizando um modelo no código de código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md) [para personalizar uma linguagem específica do domínio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
