---
title: Como exibir tipos existentes (Designer de Classe)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04b109bfa5741a5d4349f2d503bd1c821e19029d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588701"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Como exibir tipos existentes no Designer de Classe

Para ver um tipo existente e seus membros, adicione sua forma a um diagrama de classe.

Você pode ver tipos locais e referenciados. Um tipo local existe no projeto atualmente aberto e é leitura/gravação. Um tipo referenciado existe em outro projeto ou em um assembly referenciado e é somente leitura.

Para projetar novos tipos em diagramas de classe, consulte [Como: Criar tipos usando Class Designer](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Para ver tipos de um projeto em um diagrama de classes

1. A partir de um projeto no **Solution Explorer,** abra um arquivo de diagrama de classe existente (.cd). Ou, se não houver nenhum diagrama de classes, adicione um novo ao projeto. [Veja como: Adicionar diagramas de classe a projetos](how-to-add-class-diagrams-to-projects.md).

2. A partir do projeto no **Solution Explorer,** arraste um arquivo de código fonte para o diagrama da classe.

    > [!NOTE]
    > Se sua solução tiver um projeto que compartilha código por vários aplicativos, você poderá arrastar arquivos ou código para um diagrama de classe apenas das seguintes fontes:
    >
    > - Do projeto de aplicativo que contém o diagrama
    > - De um projeto compartilhado que foi importado pelo projeto de aplicativo
    > - De um projeto referenciado
    > - De um assembly

    As formas que representam os tipos definidos no arquivo de código-fonte aparecem no diagrama na posição para a qual você arrastou o arquivo.

Você também pode visualizar tipos no projeto arrastando um ou mais tipos do nó de projeto no **Class View** para o diagrama de classe.

> [!TIP]
> Se **a exibição de classe** não estiver aberta, abra a **exibição** de classe no menu **Exibir.**

Para exibir os tipos em locais padrão no diagrama, selecione um ou mais tipos na **Exibição de classe,** clique com o botão direito do mouse nos tipos selecionados e escolha **Exibir diagrama de classe**.

> [!NOTE]
> Se um diagrama de classes fechado contendo o tipo já existir no projeto, o diagrama de classes será aberto para exibir a forma do tipo. No entanto, se nenhum diagrama de classe contendo o tipo existir no projeto, o **Class Designer** criará um novo diagrama de classe no projeto e o abrirá para exibir o tipo.

Quando você exibe um tipo no diagrama pela primeira vez, sua forma aparece recolhida por padrão. É possível expandir a forma para exibir seu conteúdo.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Para exibir o conteúdo de um projeto em um diagrama de classe

Em **Solution Explorer** ou Class **View,** clique com o botão direito do mouse no projeto e escolha **Exibir**e, em seguida, escolha **Exibir diagrama de classe**. Um Diagrama de Classe populado automaticamente é criado.

## <a name="see-also"></a>Confira também

- [Como exibir herança entre tipos](how-to-view-inheritance-between-types.md)
- [Como: Personalizar diagramas de classe](how-to-customize-class-diagrams.md)
- [Visualização de tipos e relacionamentos](designing-and-viewing-classes-and-types.md)
