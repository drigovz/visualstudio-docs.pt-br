---
title: Acessibilidade em projetos do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7b80db6f8f54c897a370d53db56773ad8296f6e
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255789"
---
# <a name="accessibility-in-office-projects"></a>Acessibilidade em projetos do Office

Microsoft Visual Studio e Microsoft Office incluem muitos recursos de acessibilidade que permitem que você crie soluções personalizadas que atendam aos requisitos de acessibilidade padrão. A Microsoft publica diretrizes para acessibilidade na Web. Para obter detalhes, consulte o [site de acessibilidade](http://go.microsoft.com/fwlink/?LinkID=37113).

Na maioria dos casos, os projetos do Office no Visual Studio atendem aos padrões de acessibilidade ou expõem propriedades que podem ser definidas para tornar suas soluções acessíveis. No entanto, há alguns recursos que têm acessibilidade limitada.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Acessibilidade em tempo de design

### <a name="use-shortcut-keys-in-document-level-projects"></a>Usar teclas de atalho em projetos de nível de documento
 Quando um Microsoft Office documento do Word ou uma pasta de trabalho do Microsoft Office Excel é aberta no Visual Studio, somente um aplicativo por vez recebe os comandos de tecla de atalho. Por padrão, o Visual Studio recebe todos os comandos de tecla de atalho, mas você pode fazer com que o Word ou o Excel os receba quando o documento tiver foco, selecionando **esquema de teclado dinâmico** na página **configurações do teclado** da caixa de diálogo **Opções** . Para obter mais informações, consulte [Microsoft Office o teclado do Word, Microsoft Office configurações de teclado, caixa de diálogo opções](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) e [Microsoft Office teclado do Excel, Microsoft Office configurações de teclado, caixa de diálogo opções](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Exibir teclas de atalho para a faixa de faixas em projetos de nível de documento
 Quando um documento do Word ou uma pasta de trabalho do Excel é aberto no Visual Studio, não é possível pressionar a tecla **ALT** para exibir as teclas de atalho das guias e dos controles na faixa de palavras. Para exibir as teclas de atalho enquanto o documento ou pasta de trabalho está aberto no designer, execute as etapas a seguir.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Para exibir as teclas de atalho para guias de faixa de e controles no designer

1. No Visual Studio, no menu **ferramentas** , clique em **Opções**.

2. Expanda o nó **Ferramentas do Office** e selecione **Microsoft Office teclado do Excel** ou **Microsoft Office teclado do Word**, conforme apropriado.

3. Selecione **esquema de teclado dinâmico**.

     Uma mensagem é exibida afirmando que você deve reiniciar o Visual Studio para que a alteração entre em vigor.

4. Clique em **OK**.

5. Reinicie o Visual Studio e reabra o projeto.

6. Abra o documento ou o designer de pasta de trabalho do seu projeto.

7. Pressione **F6** para exibir as teclas de atalho para a faixa de faixas.

## <a name="accessibility-at-run-time"></a>Acessibilidade em tempo de execução

### <a name="windows-forms-controls-on-office-documents"></a>Controles de Windows Forms em documentos do Office
 Os controles de Windows Forms expõem propriedades de acessibilidade para fornecer informações sobre o controle para auxílios de acessibilidade, como leitores de tela. Você pode aproveitar essas propriedades de acessibilidade quando os controles estiverem em um documento do Office em uma personalização no nível do documento. Para obter mais informações, consulte [fornecer informações de acessibilidade para controles em um Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 No entanto, há algumas limitações de acessibilidade em tempo de execução quando Windows Forms controles são hospedados em uma pasta de trabalho do Excel ou em um documento do Word:

- Não é possível tabular de um controle para outro.

- Os controles em um documento são desabilitados quando você altera a configuração de zoom do documento para algo diferente de 100%.

  Para obter informações sobre limitações de controles de Windows Forms em documentos, consulte [limitações de controles de Windows Forms em documentos do Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Painéis de ações e painéis de tarefas personalizados
 Quando um painel ações ou um painel de tarefas personalizado tem foco, você acessa controles da mesma maneira que você acessa controles em um aplicativo Windows Forms. Para mover o cursor entre o painel Ações e o documento, você pode pressionar **F6**.

 Para obter mais informações sobre painéis de ações e painéis de tarefas personalizados, consulte [visão geral do painel Ações](../vsto/actions-pane-overview.md) e [painéis de tarefas personalizados](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modos de exibição

O Visual Studio tem as seguintes limitações relacionadas aos modos de exibição:

- Os controles em um documento do Word ou planilha do Excel são desabilitados quando você altera a configuração de zoom do documento para algo diferente de 100%.

- A caixa de diálogo **novo projeto** não exibirá os controles corretamente se um usuário alterar as opções de acessibilidade do computador para **usar alto contraste**.

Você pode usar a lupa para superar essas limitações. A lupa é um utilitário de exibição no Windows que cria uma janela separada que exibe uma parte ampliada da tela.

## <a name="see-also"></a>Consulte também

- [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Acessibilidade para pessoas com deficiências](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Recursos de acessibilidade do Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)