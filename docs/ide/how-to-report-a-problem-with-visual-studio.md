---
title: Como relatar um problema com o Visual Studio
description: Saiba como relatar um problema com o Visual Studio
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8e0718eb01f422ad435492304e77d73c14b4dee
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211169"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Como relatar um problema com o Visual Studio para Mac ou com o Instalador do Visual Studio

> [!NOTE]
> Para o Visual Studio para Mac, confira [Como relatar um problema no Visual Studio para Mac](/visualstudio/mac/report-a-problem).

Você pode relatar um problema a partir do Visual Studio ou de seu instalador. A ferramenta de comentários interna permite que você adicione facilmente informações de diagnóstico que ajudam as equipes do Visual Studio a diagnosticar e corrigir os problemas. Aqui estão as etapas para relatar um problema.

1. **No Visual Studio**, selecione o ícone de comentários no canto superior direito e selecione Relatar um Problema. Você também pode acessar a ferramenta de comentários no menu **ajudar**a  >  **enviar comentários**para  >  **relatar um problema**.
![Pop-up Relatar um problema na Comunidade de Desenvolvedores do Visual Studio](media/feedback-button.png) Como alternativa, relate um problema no **Instalador do Visual Studio** se você não puder instalar o Visual Studio ou não puder acessar a ferramenta de comentários no Visual Studio.  No Instalador, selecione o ícone de comentários no canto superior direito e selecione Relatar um Problema.
![Pop-up Relatar um problema na Comunidade de Desenvolvedores do Visual Studio](media/installer.png)

1. Ao clicar em **relatar um problema** , você abrirá o navegador padrão e entrará usando a mesma conta usada para entrar no Visual Studio

   ![Entrar para relatar um problema](../ide/media/feedback-browser-top.png)

1. Comece inserindo o título descritivo do seu relatório de bugs. Deve ter pelo menos 25 caracteres.

    ![Relatar um problema](../ide/media/feedback-report.png)

1. Depois de começar a digitar, as duplicatas possíveis são mostradas no campo título

    ![Pesquisar duplicatas](../ide/media/feedback-search.png)

1. Selecione os possíveis relatórios de erros duplicados para ver se há um correspondente ao seu próprio problema. Se houver, vote para ele em vez de criar seu próprio tíquete.

    ![Vote em duplicatas](../ide/media/feedback-duplicate.png)

2. Se nenhuma duplicata for encontrada, continue inserindo uma descrição do problema. É importante ser o mais claro possível para aumentar as chances de que possamos reproduzir o bug. Certifique-se de incluir etapas claras de reprodução.

3. Se relevante para o relatório de bugs, faça uma captura de tela marcando a caixa de seleção *incluir captura de tela do Visual Studio* .

    ![Fazer uma captura de tela ](../ide/media/feedback-screenshot.png) *somente engenheiros da Microsoft podem ver a captura de tela*

    Você pode até mesmo cortar a captura de tela diretamente no navegador para remover partes confidenciais ou não relacionadas.

4. Uma das melhores maneiras de ajudar a equipe de engenharia do Visual Studio a resolver o problema é fornecer um rastreamento e arquivos de despejo de heap a serem examinados. Você pode fazer isso facilmente registrando as etapas que resultaram no bug.

    ![Registrar suas ações ](../ide/media/feedback-recording.png) *somente engenheiros da Microsoft podem ver a gravação*

5. Examine os arquivos anexados e carregue arquivos adicionais se você acreditar que ele ajudará a diagnosticar o problema.

    ![Arquivos anexados ](../ide/media/feedback-attachments.png) *somente engenheiros da Microsoft podem ver os arquivos anexados*

6. A última etapa é pressionar o botão **Submit (enviar** ). O envio do relatório o enviará diretamente para o sistema interno de relatórios de bugs do Visual Studio aguardando a triagem.

## <a name="when-further-information-is-needed"></a>Quando forem necessárias mais informações

Quando faltam informações importantes no problema, atribuímos o estado de **mais informações** . Comentamos o problema com as informações específicas de que precisamos e você receberá uma notificação por email. Se não recebermos as informações dentro de sete dias, enviaremos um lembrete. Depois disso, fechamos o tíquete após 14 dias de inatividade.

1. Siga o link no email para o relatório de problemas ou vá para meus comentários para ver todos os relatórios no estado de **mais informações** .

    ![Meus comentários](../ide/media/feedback-my-feedback.png)

1. A seleção do link fornecer mais informações no relatório de problemas o leva para uma nova tela. A partir daqui, você pode ver quais informações estão sendo solicitadas.

   ![Meus comentários](../ide/media/feedback-need-more-info.png)

1. Você pode fornecer mais informações adicionando comentários, anexos ou gravando as etapas. Essa experiência é semelhante a relatar um novo problema ou fornecer informações adicionais ao votar em um problema.

1. O engenheiro da Microsoft fazendo a solicitação recebe uma notificação sobre as informações extras fornecidas. Se ele tiver informações suficientes para investigar, o estado do problema mudará. Caso contrário, o engenheiro solicita ainda mais informações.

Você pode ver essas solicitações na tela **meus comentários** junto com todos os outros **problemas** e **sugestões**.

## <a name="search-for-solutions-or-provide-feedback"></a>Pesquisar soluções ou fornecer comentários

Se você não quiser ou não puder usar o Visual Studio para relatar um problema, há a possibilidade de que o problema já tenha sido relatado e uma solução tenha sido postada na página da [Comunidade de Desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/).

Se você não tiver um problema para relatar, mas desejar sugerir um recurso, há um lugar para fazer isso também. Para saber mais, confira a página [Sugerir um recurso](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).

## <a name="see-also"></a>Veja também

* [Diretrizes da comunidade de desenvolvedores](./developer-community-guidelines.md)
* [Opções de comentários do Visual Studio](../ide/feedback-options.md)
* [Relatar um problema com o Visual Studio para Mac](/visualstudio/mac/report-a-problem)
* [Relatar um problema com C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacidade de dados da Comunidade de Desenvolvedores](developer-community-privacy.md)