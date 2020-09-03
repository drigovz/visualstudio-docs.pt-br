---
title: 'Como: criar uma biblioteca de atividades | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662750"
---
# <a name="how-to-create-an-activity-library"></a>Como: Crie uma biblioteca de atividade
As atividades personalizados são usadas para modelar seus processos comerciais específicos em um fluxo de trabalho. O modelo biblioteca de atividade em [!INCLUDE[vs2010](../includes/vs2010-md.md)] foi fornecido para permite que você crie como atividades personalizados que usam visualmente [!INCLUDE[wfd1](../includes/wfd1-md.md)].

### <a name="to-create-a-workflow-activity-library"></a>Para criar uma biblioteca de atividade de fluxo de trabalho

1. Inicie o [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. No menu **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...**.

     A caixa de diálogo **Novo Projeto** será aberta.

3. No painel **tipos de projeto** , selecione **fluxo de trabalho** nos projetos do **Visual C#** ou **Visual Basic** agrupamentos, dependendo da sua preferência de idioma.

4. No painel **modelos** , selecione **biblioteca de atividades**.

5. Na caixa **nome** , digite um nome descritivo para o seu projeto para facilitar a identificação.

6. Na caixa **local** , digite o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7. Na caixa **solução** , digite um nome descritivo para sua solução e clique em **OK**.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console de fluxo de trabalho a uma solução existente, abra essa solução no [!INCLUDE[vs2010](../includes/vs2010-md.md)] , clique com o botão direito do mouse na solução em **Gerenciador de soluções**e selecione **Adicionar**e **novo projeto...** para abrir a caixa de diálogo **novo projeto** . Continuar conforme descrito acima neste procedimento.

8. O modelo de projeto cria uma definição de atividade em XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] abre e exibe a tela para sua atividade personalizada.

9. Arraste uma atividade da **caixa de ferramentas** para a superfície de design para incluí-la em sua atividade personalizada.

    > [!CAUTION]
    > Uma atividade é permitida você só filho no corpo da atividade personalizado; no entanto, a atividade filho pode ser uma atividade de composição, como uma atividade de <xref:System.Activities.Statements.Sequence> ou a atividade de <xref:System.Activities.Statements.Flowchart> .

## <a name="see-also"></a>Consulte Também
 [Como criar uma atividade](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)