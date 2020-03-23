---
title: UI Texto e Ajuda para O Estúdio Visual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0477a0e1994e9c3b94df13ace4c1f3b4df51039
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303123"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Texto de interface do usuário e Ajuda para Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Texto e terminologia da UI
 Texto compreensível é crucial para a ui eficaz. Os usuários de software tendem a ler os rótulos primeiro, ou seja, os mais relevantes para completar a tarefa em questão. O texto estático é lido com menos freqüência. Planeje que os usuários iniciem suas sessões de trabalho com uma rápida varredura de toda a janela, seguida de uma leitura da ui nesta ordem aproximada:

1. Controles interativos no centro

2. Botões de confirmação

3. Controles interativos encontrados em outros lugares

4. Principais instruções

5. Explicações suplementares

6. Título da janela

7. Outro texto estático no corpo principal

### <a name="usage-patterns-for-ui-text"></a>Padrões de uso para texto de IA

#### <a name="title-bar-text"></a>Texto da barra de título
 O texto da barra de título deve corresponder ao comando que gerou a ui.

#### <a name="instructional-text-helper-text"></a>Texto instrutivo (texto auxiliar)
 Em alguns diálogos, é útil fornecer instruções principais proeminentes para explicar o que fazer na janela ou na página. Isso às vezes é chamado de "texto auxiliar".

##### <a name="writing-style-rules-for-helper-text"></a>Escrever regras de estilo para texto auxiliar

- Não explique o óbvio. A menos que seja absolutamente necessário, não inclua texto instrutivo.

- O texto instrucional é sempre colocado na parte superior do diálogo e deve se referir à tarefa que está sendo executada.

- Explique precisamente aos usuários o que eles precisam fazer. Evite comunicação excessiva e redundância.

- Revise cada janela e elimine palavras e declarações duplicadas.

- Mantenha o texto instrutivo curto. Se mais informações forem necessárias para determinados usuários ou cenários, então forneça um link para um tópico conceitual detalhado online.

- Escreva seu texto para que cada palavra tenha peso e seja necessária.

- Siga as orientações existentes da Microsoft para texto e [estilo e tom](/windows/desktop/uxguide/text-style-tone)da interface do [usuário](/windows/desktop/uxguide/text-ui) .

#### <a name="supplemental-instructions"></a>Instruções suplementares
 Instruções suplementares fornecem informações adicionais que ajudam o usuário a entender controles ou agrupamentos de controle. Isso também pode incluir o texto de sugestão necessário para entender qual formato o controle de entrada está esperando. Use instruções suplementares com moderação. Reserve-os para casos em que é provável que o usuário não entenda completamente as ramificações da escolha que está fazendo.

 ![Texto suplementar no Visual Studio](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601-b_SupplementalText1")

 **Texto suplementar no Visual Studio**

 ![Texto suplementar no Visual Studio](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601-c_SupplementalText2")

 **Texto suplementar no Visual Studio**

#### <a name="infotips"></a>Dicas de informações
 Muitas vezes, o texto instrutivo pode ser muito demorado para se posicionar no lugar na ui ou pode ser útil apenas para novos usuários, sentindo-se como desordem para usuários experientes. Neste caso, o texto instrutivo/informativo deve ser colocado como uma dica de ferramenta sob uma InfoTip.

 InfoTips devem ser colocados perto dos controles aos quais estão relacionados e devem usar o ícone InfoTip específico, que é discreto, mas perceptível.

 ![InfoTip no Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Exemplo de uma InfoTip no Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Escrever regras de estilo para InfoTips

- Escreva InfoTips como frases completas. Eles exigem verbos específicos, caso de sentença e pontuação final.

- Use InfoTips para complementar suas principais instruções ou informações. Se você está apenas usando palavras diferentes para reafirmar a ideia principal, você não precisa de uma InfoTip.

- Mantenha as InfoTips curtas e doces. Use palavras pequenas e linguagem simples e cotidiana que apoie e incentive o usuário.

- Siga as orientações existentes da Microsoft para texto e [estilo e tom](/windows/desktop/uxguide/text-style-tone)da interface do [usuário](/windows/desktop/uxguide/text-ui) .

#### <a name="control-labels"></a>Etiquetas de controle
 As etiquetas de controle devem ser curtas, concisas e seguir a [orientação do Windows Desktop para Controles](/windows/desktop/uxguide/controls).

 Para obter mais informações sobre o formato e a colocação do rótulo de controle dentro da ui, consulte [Layout para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Links de ajuda
 Os links de ajuda podem ser colocados dentro do texto instrutivo ou no corpo da ui. Eles podem ser links para ajuda ou iniciar diálogos internos.

##### <a name="visual-style-rules-for-help-links"></a>Regras de estilo visual para links de ajuda

- Use as cores corretas do ambiente para hiperlinks. Um hiperlink devidamente estilizado não piscará brevemente em vermelho quando clicado. Se você ver isso, então é uma indicação de que as cores do ambiente não estão sendo usadas.

- Os sublinhados só devem ser usados no hover ou quando o link estiver incorporado em um parágrafo.

- Para obter informações mais detalhadas sobre estilos visuais e de interação para hiperlinks, consulte Botões e hiperlinks.

##### <a name="writing-style-rules-for-help-links"></a>Escrever regras de estilo para links de ajuda

- Ao iniciar diálogos, mantenha os padrões para elipses: sem elipses para navegação, elipses se a tarefa exigir ui adicional.

     ![Link de ajuda no Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601-e_HelpLink")

     **Uma elipse (...) em um link de Ajuda indica que a tarefa exigirá ui adicional.**

- Os links não devem começar com "Learn", pois essa não é a intenção do usuário. O usuário quer responder a uma pergunta específica, não receber uma educação geral.

- Frase ajuda links para que eles façam a pergunta que o tema irá responder.

     Incorreto: "Saiba mais sobre os preços do Windows Azure Mobile Services"

     Correto: "Quais opções de preços estão disponíveis para o Windows Azure Mobile Services?"

- Nunca use *Clique...* no texto do link.

- Nunca ligue apenas a palavra "aqui". Isso é problemático para alguns leitores de tela, que vão dublar apenas a palavra hiperligada.

     Incorreto: "Encontre informações sobre os Serviços Móveis do Windows Azure **aqui"**

     Correto: "Quais opções de preços estão disponíveis para o Windows Azure Mobile Services?"

- Para obter mais informações sobre o estilo de escrita correto para links de ajuda, consulte a [orientação do Windows Desktop para ajuda](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Texto de sugestão
 O texto de sugestão aparece como uma marca d'água dentro de um controle ou abaixo do controle. A formatação correta será aplicada usando o token VSColors apropriado, `Environment.GrayText`.

 Pode aparecer em várias formas.

- No lugar do rótulo de controle:

     ![Texto de dica no Visual Studio](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601-f_HintText1")

- Com um verbo, dando instruções:

     ![Texto de dica no Visual Studio](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601-g_HintText2")

- Com texto indicando uma entrada necessária:

     ![Texto de dica no Visual Studio](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Texto de marca d'água
 Em uma superfície de design vazia, o texto deve indicar o que fazer, bem como fornecer links para abrir outras janelas relacionadas, se apropriado:

 ![Texto de marca d'água no Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601-i_WatermarkText")

 **Exemplo de texto de marca d'água no Visual Studio**

### <a name="common-terminology"></a>Terminologia comum

|Termo|Explicação|Comentário|
|----------|-----------------|-------------|
|Faça login / Faça login|Verbos usados sinônimo de web para representar autenticação em uma propriedade web. Dentro dos clientes, usamos isso uma vez como uma noção de alto nível para entrar e sair da conexão de usuário IDE, que representa uma identidade de alto nível que fornece recursos de nível superior, como roaming e licenciamento que não estão disponíveis com todas as outras conexões.|O Usuário IDE é o único recurso que deve representar um verbo de entrada/saída de login, pois representa o usuário IDE de alto nível.|
|Conectar / desconectar|Use em locais onde um recurso mantém uma única conexão a um serviço online.|O Server Explorer, onde você só pode ter uma conexão Ativa Azure por vez, é um exemplo de Conexão/Desconexão.|
|Adicionar / Remover|Não destrutivo. Use ao adicionar ou remover algo de uma lista.|A caixa de diálogo da lista de servidores do GERENCIADOr de conexões DO TFS é um exemplo de Adicionar/Remover.|
|Excluir|Destrutivo. Use somente quando o elemento que está sendo removido será permanentemente descartado ou excluído do disco.|"Excluir" geralmente requer um prompt se o resultado estiver excluindo um arquivo do disco.|

## <a name="error-messages"></a>Mensagens de erro

### <a name="overview"></a>Visão geral
 Erros acontecem. Definir limitações sobre o que o usuário pode fazer é um primeiro passo sensato para evitar mensagens de erro evitáveis. No entanto, quando um erro ocorre, uma mensagem de erro bem escrita pode ir longe para mitigar o problema. As mensagens de erro são, sem dúvida, um dos tipos mais importantes de notificação que o usuário vê, pois são síncronas e indicam um problema que precisa ser resolvido. Mensagens de erro mal escritas deixam os usuários por conta própria para decidir a causa dos erros e quaisquer soluções possíveis.

 Os usuários podem parar de prestar atenção às mensagens de erro usadas ou confusas, por isso escreva apenas mensagens necessárias que agreguem valor à experiência do usuário. Se a mensagem for simplesmente uma notificação, use uma apresentação alternativa.

### <a name="rules-for-creating-an-error-message"></a>Regras para criar uma mensagem de erro

- Ao construir mensagens de erro, escolha o nível de erro apropriado para o público. Procure resumos simples que forneçam uma ação que o usuário possa tomar, se aplicável. Não indfique nada que o usuário não precise saber.

- Providencie assistência construtiva. É mais fácil ler e agir em uma mensagem de erro que contém instruções.

- Não use negativos duplos.

- Execute uma gramática automatizada e manual e uma verificação ortográfica em qualquer mensagem de erro que você escrever.

- Para mensagens de erro complexas, evite comunicações seqüenciais. Nunca use uma conexão de F1 para a mensagem de erro. A mensagem em si deve ser suficiente.

- Use o ícone correto.

- Torne as perguntas fáceis de entender e use botões que tenham escolhas claras, como "Excluir" e "Cancelar".

- Para avisos, seja claro sobre qual será a consequência do processo. Os botões devem indicar a conseqüência.

- Para erros, descreva o que o usuário pode fazer para corrigir o problema. Botões devem ser ações ou dizer "Fechar". Não use um botão "OK" para uma mensagem de erro.

- Algumas perguntas a se fazer ao construir uma mensagem de erro:

  - O usuário pode descobrir como resolver o problema apenas com esse erro?

  - O usuário usa o mesmo vocabulário que esse erro?

  - Esse erro é ambíneo ou compartilhado em várias situações? Se sim, como você orienta os usuários para a solução de que eles precisam?

#### <a name="build-errors"></a>Erros de compilação
 Como o Visual Studio é uma ferramenta de desenvolvimento de software, muitos de seus componentes têm uma etapa de compilação, conversão ou codificação para converter o trabalho do desenvolvedor em forma binária. Essas conversões podem causar erros quando o compilador não pode processar arquivos de autoria inadequada ou quando as opções de compilador não foram definidas corretamente.

 Os usuários do Visual Studio podem gastar um enorme número de horas de desenvolvimento resolvendo erros de compilação. Esse tempo de resolução aumenta quando erros têm dependências ou quando mensagens de erro são mal escritas, o que pode dificultar a descoberta da fonte do erro.

 Os melhores erros de compilação são aqueles que não ocorrem em primeiro lugar, e é por isso que o Visual Studio fornece squiggles AutoComplete e IntelliSense. Validadores de esquemas e ferramentas similares fornecem o mesmo tipo de feedback. Esses mecanismos orientam proativamente o usuário a construir códigos bem formados, diminuindo a chance de erros de construção.

 O Visual Studio fornece uma janela de ferramentas onde os usuários podem ler e navegar através dos erros que ocorreram em suas janelas de documentos. Os atalhos do teclado são fornecidos para que o usuário possa navegar rapidamente em grandes quantidades de código e ir diretamente para o local do problema. O Visual Studio também permite que cada erro de compilação seja vinculado a uma determinada Palavra-chave de Ajuda/ID de contexto para que o usuário possa ir diretamente para um tópico de Ajuda que fornece informações mais detalhadas sobre o erro.

 Escreva erros de compilação claros e concisos:

- **Use linguagem simples** que explique o problema com pouco ou nenhum jargão compilador. O texto de um erro de compilação não deve ser excessivamente técnico.

- **Esboçar possíveis causas.** Por exemplo, "Falta um cólon entre a propriedade e o valor na declaração '(propriedade) : (valor)'."

- Dê detalhes sobre possíveis correções. Se não houver espaço suficiente, então detalhes adicionais podem ser colocados no tópico de Ajuda correspondente.

### <a name="components-of-a-well-written-error-message"></a>Componentes de uma mensagem de erro bem escrita

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Use o serviço de diálogo shell para mensagens de erro.
 O uso do serviço de diálogo shell permite controlar a aparência da mensagem, fontes em particular, sem grandes alterações em elementos individuais. Use os mecanismos **IErrorInfo** e reporte-os usando **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Escolha uma apresentação de notificação eficaz e apropriada.
 Use um diálogo modal com um aviso crítico se for necessária uma ação imediata para evitar a perda de dados (notificação síncrona). Ícones críticos são reservados para situações em que fechar a mensagem sem lê-la pode levar a consequências negativas. A perda de dados é uma situação crítica que requer uma resposta em nível de alarme. O uso excessivo do ícone crítico dessensibiliza os usuários à sua importância. Se a mensagem de erro for de natureza informativa, considere alternativas para uma caixa de diálogo modal (notificação assíncrona).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Fornecer uma explicação limpa e sucinta do porquê o problema ocorreu em vez de uma explicação técnica.
 Sobrecarregar os usuários com detalhes técnicos na explicação os tornará mais propensos a ignorar mensagens de erro. Exemplos de boas mensagens:

- "Incapaz de abrir o arquivo solicitado."

- "Incapaz de se conectar à Internet."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Forneça informações sobre como corrigir o problema.
 Ofereça ao usuário sugestões de como corrigir o problema. Seja honesto com o usuário se não houver sugestões. Forneça links diretos para fontes on-line alternativas, como suporte técnico ou suporte à comunidade. Tente apontar os usuários para informações on-line específicas pertinentes ao problema. Para obter um ID de erro, considere vincular os usuários a um segmento de discussão sobre esse erro específico. Exemplos de boas mensagens:

- "Certifique-se de que você está conectado à Internet e tente esta operação novamente."

- "Certifique-se de que o arquivo existe e que você tem permissão para abri-lo."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Escreva uma mensagem curta e direta.
 Uma mensagem de erro pode notificar, explicar e oferecer uma solução, mas ainda assim ser ignorada se for muito falada. Uma solução é usar a divulgação progressiva com um botão de detalhes. Por exemplo, dê uma breve descrição/solução e, em seguida, coloque mais detalhes em um botão de detalhes. Se os usuários optarem por ler mais informações sobre o erro, eles podem fazê-lo.

 O idioma na mensagem deve ser:

- **Apropriado para o domínio.** Use a linguagem que o usuário entenderá. Mesmo que nossos clientes sejam desenvolvedores, eles muitas vezes não têm o contexto e a terminologia que temos.

- **Específico.** Evite palavras vagas e dê nomes e locais específicos dos objetos envolvidos. Por exemplo, uma mensagem de erro como "caractere é inválido" não é útil. Qual personagem? "Arquivo não encontrado." Qual arquivo?

- **Cortês.** Não culpe o usuário ou faça-os se sentirem estúpidos. Evite linguagem hostil ou ofensiva (matar, executar, terminar, fatal, ilegal). Evite textos maiúsculos, que muitas vezes são vistos como gritos e não são tão legíveis. Não use humor.

- **Correto.** Use ortografia correta e gramática (mesmo em alfas). Erros de digitação não são profissionais e embaraçosos.

- **Contextualmente apropriado.** Use o texto do botão apropriado. Evite o botão "OK" e, em vez disso, use "Continuar" ou "Sim/Não".

### <a name="error-message-examples"></a>Exemplos de mensagens de erro

|Bom|Incorreto|
|----------|---------|
|"O número que você discou não está mais em serviço. Por favor, verifique o número e disque novamente ou disque 0 para o operador."|- "Erro (449): Número ilegal"<br />- "Este erro de exceção não manuseado indica que a operação foi concluída com sucesso."<br /><br /> ![Mensagem de erro ruim no Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Acessando a ajuda

### <a name="overview"></a>Visão geral
 Além da documentação no MSDN, um usuário do Visual Studio tem vários pontos de acesso para auxiliar o usuário enquanto estiver na ui. Para garantir que esses pontos de acesso estejam consistentemente disponíveis, as equipes de recursos precisam aproveitar o sistema de ajuda oferecido pelo ambiente. Estes pontos de acesso são:

- **Texto instrutivo e suplementar em diálogos.** Texto estático que dá direção ou explicação, seja na superfície da ia ou disponível no mouse sobre um ícone infotip.

- **F1 Help** (somente editor). Dentro do editor do Visual Studio, um usuário pode confiar que, a qualquer momento, pressionar a F1 trará um tópico de Ajuda específico para a seleção atual. Certifique-se de que os tópicos associados à F1 sejam apropriados e informativos.

- **Hiperlinks para tópicos de ajuda.** Um hiperlink dentro de uma superfície de diálogo, janela de ferramenta ou design que lança um tópico para ajudar o usuário a aprender mais sobre uma tecnologia, capacidade ou informações sobre como realizar uma tarefa.

- **Mecanismos de IU auxiliares, como tags inteligentes e diálogos de construção.** Esses mecanismos auxiliam o usuário a entender um elemento de IA ou facilitar uma tarefa, como tags inteligentes ou diálogos de construtores.

- **Botões de ajuda de ui** (preteridos). Um indicador visível na barra de título que dá acesso ao tópico de Ajuda da F1 relacionado.

### <a name="text"></a>Texto

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Texto instrutivo e suplementar em diálogos
 Em diálogos que suportam tarefas complexas, pode haver a necessidade de dar texto instrutivo dentro da UI, muitas vezes no topo do diálogo ou controles próximos complexos. Consulte [o texto e a terminologia](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) da UI para obter detalhes sobre o estilo de escrita.

#### <a name="infotips"></a>Dicas de informações
 Muitas vezes, o texto instrutivo pode ser muito demorado para se posicionar na ui ou pode ser útil apenas para novos usuários, sentindo-se como desordem para usuários experientes. Neste caso, o texto instrutivo/informativo deve ser colocado como uma dica de ferramenta uma InfoTip.

 InfoTips devem ser colocados perto dos controles aos quais estão relacionados e devem usar o ícone InfoTip específico, que é discreto, mas perceptível.

 ![InfoTip no Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601-d_InfoTip")

 **Exemplo de uma InfoTip no Visual Studio**

### <a name="interactive-help-mechanisms"></a>Mecanismos interativos de ajuda

#### <a name="f1-help"></a>Ajuda F1
 A F1 Help é necessária dentro de um editor ou superfície de design, mas não em outros lugares no ambiente do Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hiperlinks para tópicos de ajuda
 Os hiperlinks podem ser usados para executar uma ação, navegar dentro do IDE ou iniciar ajuda em um navegador. Consulte [o texto e a terminologia da UI](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) para obter detalhes sobre o idioma e botões e hiperlinks de 07.10.01 e hiperlinks para orientações visuais e de layout.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Botões de ajuda [?] nas barras de título de diálogo (depreciadas)
 Na maioria das vezes, os botões Ajuda [?] na barra de título das diálogos são preteridos. Os tópicos de IA não fazem mais parte do nosso modelo de doc e, portanto, pode não haver um tópico relevante para vincular. Essencialmente, o botão da barra de título era a mesma coisa que o F1 Help, e isso não é mais necessário nos diálogos. Em alguns casos, isso ainda pode ser usado como um indicador de que há informações mais conceituais ou processuais disponíveis, embora hiperlinks sejam mais comumente usados em iu mais recentes.

##### <a name="dialogs-created-through-the-environment"></a>Diálogos criados através do meio ambiente
 Muitos diálogos de shell são criados através da função **VBDialogBoxParam.** Esta função compartilhada foi atualizada para ajudar a mover o botão **Ajuda** da caixa de diálogo para o **?** botão mantendo uma arquitetura que é retrocompatível e extensível.

 Especificamente, a função **VBDialogBoxParam** analisa o modelo de diálogo para um botão cujo ID é **IDHELP** (9) ou o rótulo é **Ajuda** ou **ajuda&**. Se um botão de Ajuda for encontrado, ele será oculto e o estilo **WS_EX_CONTEXTHELP** será adicionado à caixa de diálogo, qual coloca o **?** botão na barra de título da caixa de diálogo.

 Quando a caixa de diálogo é criada, ela empurra o diálogo proc para uma pilha e invoca a caixa de diálogo com um proc de diálogo de pré-processamento chamado **DialogPreProc**. Quando **o?** botão é clicado, ele envia um **WM_SYSCOMMAND** de **SC_CONTEXTHELP** para a caixa de diálogo. O **DialogPreProc** captura este comando e o altera para uma **mensagem WM_HELP,** que é passada para o proc de diálogo original.

 A maioria dos diálogos criados pelo ambiente tem um botão Ajuda na caixa de diálogo. Quando a caixa de diálogo é exibida, o botão Ajuda é automaticamente oculto e apenas o **?** botão funciona. Se **o?** botão é sempre removido ou alterado no Windows, esta solução permite que você se mova rapidamente para os botões de Ajuda originais.

 Esta solução faz quatro suposições que podem causar bugs:

- O botão de ajuda da caixa de diálogo é **IDHELP** (9).

- A caixa de diálogo parece correta quando o botão Ajuda está oculto.

- O diálogo não substitui seu winproc.

- O diálogo não está incorporado dentro de outro diálogo.

  Se a sua caixa de diálogo residir no msenv e não usar **o VBDialogBoxParam,** investigue o **vbdialogBoxParam** antes de implementar o seu próprio manipulador.

##### <a name="dialogs-created-through-other-packages"></a>Diálogos criados através de outros pacotes
 Você pode implementar sua própria solução para diálogos que residem fora do msenv. Para uma classe de diálogo compartilhada em seu VSPackage, considere mover o botão para a barra de título ou implementar um manipulador em cada diálogo. O código a seguir é um esqueleto de uma implementação para ajudá-lo a começar:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Botões de ajuda em código gerenciado
 Sobrepor a barra de título da janela O comportamento padrão do botão de ajuda é fácil no código gerenciado. Abaixo está um aplicativo de demonstração completo que demonstra esse comportamento. Em essência, você precisa substituir o método **WndProc** do seu formulário e, em seguida, disparar as solicitações de ajuda da F1 quando uma mensagem **de SC_CONTEXTHELP** é interceptada.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Confira também
- [Fontes e formatação para Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Layout para Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Notificações e progresso do Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
