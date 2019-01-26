---
title: 'Designer de fluxo de trabalho - como: Adicionar atividades à caixa de ferramentas'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1348e958fa4b4871036794238ea3fb19fddb5745
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983814"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Como: Adicionar atividades à caixa de ferramentas

As atividades podem ser adicionadas para o **caixa de ferramentas** em sua solução de várias maneiras diferentes. Você pode adicioná-los do seu projeto atual, referênciá-los de um projeto diferente, ou referênciá-los de um conjunto diferente.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Para adicionar uma atividade do seu projeto atual

1.  Adicionar uma nova atividade personalizado ao seu projeto atual de fluxo de trabalho. Para obter mais informações sobre como adicionar uma nova atividade personalizado ao seu projeto, consulte [como: Adicionar um novo Item a um projeto de fluxo de trabalho](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Adicione lógica personalizada para a atividade.

3.  Compile o projeto. Se o build foi bem-sucedido, uma nova categoria na **caixa de ferramentas** denominado "\<*nome do projeto*>" com a atividade personalizado incluída na categoria é exibida.

    > [!NOTE]
    > Se a caixa de ferramentas é reiniciada, as atividades personalizados serão removidas, mesmo se a solução é compilado novamente. Para preencher novamente a caixa de ferramentas com atividades personalizados depois que ele foi redefinido, reinicie o Visual Studio.

    > [!NOTE]
    > A caixa de ferramentas só pode mostrar uma atividade de um determinado nome. Se duas atividades diferentes assemblies com o mesmo nome de classe, somente um exibirá.

    > [!NOTE]
    > O domínio de aplicativo é compartilhado entre instâncias do editor; se as variáveis estáticas são usados, serão compartilhados entre instâncias do editor também. Se esse não é o comportamento desejado, um serviço deve ser usado para controlar instâncias variáveis. Ver [usando o contexto de edição de ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) para obter informações sobre como usar serviços dentro do designer.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Para adicionar uma atividade de dentro de um projeto diferente

1.  Abra uma solução que contém pelo menos um projeto de fluxo de trabalho e um projeto personalizado de biblioteca de atividade ou outro projeto de fluxo de trabalho que define uma atividade personalizado.

2.  Criar ambos os projetos. Se as compilações foram bem-sucedidas, uma nova categoria na **caixa de ferramentas** denominado "\<*nome do projeto*>" com a atividade personalizado incluída na categoria é exibida.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Para adicionar uma atividade à caixa de ferramentas de um assembly

1.  Abra uma solução de fluxo de trabalho.

2.  Dos **ferramentas** menu, selecione **Choose Toolbox Items**.

3.  No **Choose Toolbox Items** caixa de diálogo, selecione o **componentes de System. Activities** guia e clique em **procurar** para navegar até o assembly que contém o personalizado atividade que você deseja adicionar.

4.  Selecione o assembly e clique em **Okey**. O componente personalizado de atividade é adicionado à lista de componentes e automaticamente selecionado.

    1.  Clique em **Okey** para fechar a caixa de diálogo.

5.  Para exibir a caixa de ferramentas, selecione **caixa de ferramentas** da **exibição** menu.

6.  A atividade personalizada é exibida na **caixa de ferramentas** sob a categoria que estava em foco antes que o item foi adicionado. Por exemplo, se o **geral** selecionada na categoria a **caixa de ferramentas** antes de adicionar o item de caixa de ferramentas, a atividade aparece sob o **geral** categoria.

## <a name="see-also"></a>Consulte também

- [Usando o Designer de Fluxo de Trabalho](developing-applications-with-the-workflow-designer.md)