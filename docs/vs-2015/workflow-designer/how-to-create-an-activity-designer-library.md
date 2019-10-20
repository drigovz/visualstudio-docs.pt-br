---
title: 'Como: criar uma biblioteca do designer de atividade | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662865"
---
# <a name="how-to-create-an-activity-designer-library"></a>Como: Crie uma biblioteca do designer de atividade
Designers personalizados de atividade permitem que você crie uma interface de usuário para uma atividade padrão ou personalizado. Você controla a complexidade da interface do usuário e tem a capacidade de criar mais de um designer de atividade para uma atividade. Este cenário permite que você crie os designers que são personalizados para mais audiências.

### <a name="to-create-an-activity-designer-library"></a>Para criar uma biblioteca do designer de atividade

1. Inicie o [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. No menu **arquivo** , aponte para **novo**e, em seguida, selecione **projeto...** para abrir a caixa de diálogo **novo projeto** .

3. No painel **tipos de projeto** , selecione **fluxo de trabalho** do **Visual C#**  ou **Visual Basic** agrupamentos, dependendo de seu idioma preferido.

4. No painel **modelos** , selecione **biblioteca do designer de atividade**.

5. Na caixa **nome** , insira um nome descritivo para o seu projeto para facilitar a identificação.

6. Na caixa **local** , insira o diretório no qual você deseja salvar o projeto ou clique em **procurar** para navegar até ele.

7. Na caixa **solução** , digite um nome descritivo para sua solução e clique em **OK**.

    > [!NOTE]
    > Se você quiser adicionar um aplicativo de console de fluxo de trabalho a uma solução existente, abra essa solução no [!INCLUDE[vs2010](../includes/vs2010-md.md)], clique com o botão direito do mouse na solução em **Gerenciador de soluções**e selecione **Adicionar**e **novo projeto...** para abrir a caixa de diálogo **novo projeto** . Continuar conforme descrito acima neste procedimento.

8. O modelo de projeto cria uma definição de designer de atividade em XAML e o arquivo de código de implementação no código-fonte. [!INCLUDE[wfd1](../includes/wfd1-md.md)] abre e exibe a tela para o designer de atividade.

9. Arraste [!INCLUDE[avalon1](../includes/avalon1-md.md)] controles da **caixa de ferramentas** para a superfície de design para usá-los em seu designer de atividade personalizado.  Para obter um exemplo de como implementar um designer de atividade personalizado, consulte [como: criar um designer de atividade personalizado](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Os designers de atividades personalizadas podem ser usados para atividades personalizadas, bem como para [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]activities padrão.

## <a name="see-also"></a>Consulte também
 [Criando um projeto de fluxo de trabalho](../workflow-designer/creating-a-workflow-project.md)