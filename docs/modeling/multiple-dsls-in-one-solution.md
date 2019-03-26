---
title: Várias DSLs em uma mesma solução
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c894ce7466c253916794495649fa65d703e6d67
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416143"
---
# <a name="multiple-dsls-in-one-solution"></a>Várias DSLs em uma mesma solução

É possível empacotar diversas DSLs como parte de uma única solução para serem instaladas juntas.

É possível usar diversas técnicas para integrar múltiplas DSLs. Para obter mais informações, consulte [integrando modelos por meio do Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [como: Adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md) e [Personalizando o comportamento de cópia](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Criar mais de uma DSL na mesma solução

1. Criar um novo **VSIX Project** projeto.

2. Crie dois ou mais projetos DSL no diretório da solução VSIX.

   - Abra uma nova instância do Visual Studio para cada DSL. Crie a nova DSL e especifique a mesma pasta da solução que a solução VSIX.

   - Certifique-se de criar cada DSL com uma extensão de nome de arquivo diferente.

   - Alterar os nomes da **Dsl** e **DslPackage** projetos para que eles estejam todos diferentes. Por exemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Em cada **DslPackage\*\source.extension.tt**, atualize essa linha para o nome do projeto Dsl correto:

      `string dslProjectName = "Dsl2";`

   - Na solução VSIX, adicione o Dsl * e DslPackage\* projetos. É aconselhável colocar cada par em sua própria pasta da solução.

2. Combine os manifestos VSIX das DSLs:

   1.  Abra _YourVsixProject_**\source.extension.manifest**.

   2.  Para cada DSL, escolha **adicionar conteúdo** e adicione:

       -   `Dsl*` um projeto como um **componente MEF**

       -   `DslPackage*` um projeto como um **componente MEF**

       -   `DslPackage*` um projeto como um **VS Package**

3. Compile a solução.

   O VSIX resultante instalará as duas DSLs. Você pode testá-las usando F5 ou implantar _YourVsixProject_**\bin\Debug\\\*. VSIX**.

## <a name="see-also"></a>Consulte também

- [Integrando modelos por meio do Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Como: Adicionar um manipulador do tipo "arrastar e soltar"](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Personalizando o comportamento de cópia](../modeling/customizing-copy-behavior.md)