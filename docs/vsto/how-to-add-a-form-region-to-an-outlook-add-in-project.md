---
title: 'Como: Adicionar uma região de formulário a um projeto de suplemento do Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 139cdb0314783c76352cc499256fb89610354843
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083940"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Como: Adicionar uma região de formulário a um projeto de suplemento do Outlook
  Criar uma região de formulário para estender um formulário personalizado ou padrão do Microsoft Office Outlook usando o **nova região de formulário do Outlook** assistente. Você pode criar uma nova região de formulário e projetar a interface do usuário no Visual Studio, ou você pode importar de uma região de formulário que foi projetada no Outlook e adicione o código do Visual Basic ou c#.

 Se você tiver uma região de formulário do Outlook que você usou em outro projeto do Outlook, você pode reutilizá-lo em seu projeto de suplemento do VSTO do Outlook atual usando o **Add Existing Item** caixa de diálogo. Para obter mais informações, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Para adicionar uma nova região de formulário a um projeto do Outlook

1. Abra ou crie um projeto de suplemento do VSTO do Outlook no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, confira [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na **Gerenciador de soluções**, selecione o nó do projeto do suplemento do VSTO do Outlook.

3. No menu **Projeto**, clique em **Adicionar Novo Item**.

4. No **Adicionar Novo Item** caixa de diálogo, selecione **região de formulário do Outlook**.

5. Digite um nome para a região do formulário na **nome** caixa e, em seguida, clique em **Add**.

     O **região do formulário NewOutlook** assistente é iniciado.

6. Sobre o **selecione como você deseja criar a região do formulário** , selecione se deseja criar a região do formulário. basta arrastar controles gerenciados em um designer visual ou importar uma região de formulário que foi projetada no Outlook.

    > [!NOTE]
    >  Se você optar por importar de uma região de formulário que foi projetada no Outlook e, em seguida, você deve especificar o local de um armazenamento de formulário do Outlook (*ofs*) arquivos. Você não pode adicionar controles gerenciados em uma região de formulário que você cria no Outlook; Você só pode adicionar o código por trás da interface do usuário existente. Para obter mais informações, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).

7. Sobre o **selecione o tipo da região de formulário que você deseja criar** página, examine os tipos de região de formulário, selecione um e, em seguida, clique em **próxima**. Para obter mais informações sobre os tipos de região de formulário, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).

8. Sobre o **fornecer um texto descritivo e selecionar suas preferências de exibição** página, o **nome** , digite um nome para a região do formulário. Para os tipos de região de formulário de substituir tudo, de substituição e o **Title** e **descrição** caixas também estão disponíveis.

     Para obter informações sobre onde o nome, título e descrição aparecem no Outlook quando você implanta a região do formulário, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).

9. Selecione um ou mais modos de exibição no qual você deseja que a região do formulário seja exibido.

     Todos os tipos de região do formulário podem aparecer em inspetores, no modo (para a criação de itens) de redação e no modo de leitura (para exibir itens). Adjacente, substituição e tipos de região de formulário de substituir tudo também podem aparecer no painel de leitura.

10. Clique em **Avançar**.

11. Sobre o **identificar as classes de mensagem que exibirão esta região do formulário** página, selecione as classes de mensagem do Outlook padrão ou digite os nomes das classes de mensagem personalizada de um ou mais e, em seguida, clique em **concluir**. Para obter mais informações, consulte [associar uma região de formulário uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Consulte também
- [Acessar uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)
- [Soluções do Outlook](../vsto/outlook-solutions.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Diretrizes para criar regiões de formulário do Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Passo a passo: Criar uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Passo a passo: Importar de uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Personalizar ações em regiões de formulário do Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
