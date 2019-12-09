---
title: Várias DSLs em uma solução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668563"
---
# <a name="multiple-dsls-in-one-solution"></a>Várias DSLs em uma mesma solução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

É possível empacotar diversas DSLs como parte de uma única solução para serem instaladas juntas.

 É possível usar diversas técnicas para integrar múltiplas DSLs. Para obter mais informações, consulte [integrando modelos usando o Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md) e [Personalizar o comportamento de cópia](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Compilar mais de uma DSL na mesma solução

1. Crie duas ou mais soluções DSL e um projeto VSIX e adicione todos os projetos a uma única solução.

   - Para criar um novo projeto VSIX: na caixa de diálogo **novo projeto** , **selecione C#Visual** , **extensibilidade**, **projeto VSIX**.

   - Crie duas ou mais soluções DSL no diretório da solução VSIX.

        Abra uma nova instância do Visual Studio para cada DSL. Crie a nova DSL e especifique a mesma pasta da solução que a solução VSIX.

        Certifique-se de criar cada DSL com uma extensão de nome de arquivo diferente.

   - Altere os nomes dos projetos **DSL** e **DslPackage** para que eles sejam todos diferentes. Por exemplo: `Dsl1`, `DslPackage1`, `Dsl2` `DslPackage2`.

   - Em cada **DslPackage \* \ Source.Extension.tt**, atualize essa linha para o nome do projeto DSL correto:

        `string dslProjectName = "Dsl2";`

   - Na solução VSIX, adicione os projetos de \* de DSL * e DslPackage.

        É aconselhável colocar cada par em sua própria pasta da solução.

2. Combine os manifestos VSIX das DSLs:

   1. Abra _YourVsixProject_ **\Source.Extension.manifest**.

   2. Para cada DSL, escolha **adicionar conteúdo** e adicionar:

       - `Dsl*` projeto como um **componente MEF**

       - `DslPackage*` projeto como um **componente MEF**

       - `DslPackage*` projeto como um **pacote do vs**

3. Compile a solução.

   O VSIX resultante instalará as duas DSLs. Você pode testá-los usando F5 ou implantar _YourVsixProject_ **\bin\Debug \\ \*. vsix**.

## <a name="see-also"></a>Consulte também
 [Integrando modelos usando o Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md) [Personalizando o comportamento de cópia](../modeling/customizing-copy-behavior.md)
