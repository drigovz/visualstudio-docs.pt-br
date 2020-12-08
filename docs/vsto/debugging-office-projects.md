---
title: Depurar projetos do Office
description: Saiba como você pode depurar projetos do Office usando as mesmas ferramentas de Microsoft Visual Studio que você usa para outros projetos do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea4874effcba4ee948f921ae9bf91f145b661f4f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845629"
---
# <a name="debug-office-projects"></a>Depurar projetos do Office
  Você pode depurar projetos do Office usando as mesmas ferramentas da Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usadas para outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] os recursos do depurador, como a capacidade de inserir pontos de interrupção e variáveis de exibição na janela **locais** , também estão disponíveis quando você depura projetos do Office. Para obter mais informações sobre [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ferramentas de depuração, consulte [depurar no Visual Studio](../debugger/debugger-feature-tour.md).

> [!TIP]
> Para simplificar a depuração, feche todas as instâncias abertas do aplicativo do Office antes de criá-las e depurá-las.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Iniciar e parar o depurador
 Você pode começar a depurar um projeto do Office da mesma forma que inicia a depuração de outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos; por exemplo, você pode pressionar a tecla **F5** . Quando você inicia a depuração de um projeto de suplemento do VSTO, um novo processo para o aplicativo do Office de destino é iniciado e o suplemento do VSTO é carregado.

 Quando você inicia a depuração de um projeto de nível de documento, o documento ou pasta de trabalho é aberto em um novo processo do Word ou do Excel.

 Quando você interrompe o depurador, o depurador encerra o processo do aplicativo abruptamente ou desanexa se você tiver o depurador definido como Desanexar. Todos os outros documentos que estão abertos no processo de aplicativo do Office encerrado também são fechados sem aviso e todas as alterações não salvas são perdidas. Isso pode incluir todos os documentos ou pastas de trabalho que são abertos enquanto o depurador está em execução.

 Normalmente, é melhor desanexar do processo antes de parar o depurador, para que você possa encerrar o aplicativo do Office da maneira normal. Você também pode desanexar do processo primeiro se ainda quiser trabalhar com um documento aberto ou uma planilha depois de parar o depurador.

 Se você estiver Depurando uma personalização em nível de documento para o Word, interrompendo repetidamente o depurador e fazendo com que o Word feche repentinamente pode levar ao modelo normal se tornando corrompido. Se isso acontecer, você poderá excluir o modelo normal corrompido e ele será recriado automaticamente na próxima vez que abrir o Word. No entanto, todas as macros que foram armazenadas no modelo normal não são recriadas.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Depurar os suplementos do VSTO do Office 2013 usando o Office 2013 ou o Office 2016
 Se você estiver usando o Visual Studio 2015 e tiver as duas versões do Office instaladas lado a lado, o Visual Studio iniciará o Office 2016. Se você estiver usando Visual Studio 2013, o Visual Studio iniciará o Office 2013.

 Se você quiser depurar seu suplemento do VSTO usando uma versão diferente do Office (2013 ou 2016), abra o **Designer de projeto** e, na guia **depurar** , escolha o botão de opção **Iniciar programa externo** . Em seguida, navegue até o local do executável do aplicativo do Office apropriado.

## <a name="f10-and-f11-behavior"></a>Comportamento F10 e F11
 Quando você começa a depurar um projeto do Office, **F10** e **F11** não têm o mesmo comportamento que quando você inicia a depuração de outros projetos Visual Basic ou C#. Em projetos Visual Basic ou C#, o depurador para para a função main; em projetos do Office, o Visual Studio não tem controle sobre a função principal do aplicativo do Office. No entanto, durante a depuração, **F10** e **F11** têm as mesmas funções que nos projetos Visual Basic e C#.

## <a name="display-exceptions"></a>Exibir exceções
 Devido à maneira como o código gerenciado interage com código não-gerenciado, o Visual Studio não exibe erros que são lançados por Microsoft Office aplicativos. Por exemplo, se um suplemento do VSTO criado usando as ferramentas de desenvolvimento do Office no Visual Studio lançar uma exceção, a Microsoft Office aplicativo continuará sem exibir um erro. Para ver esses erros, defina o depurador para interromper Common Language Runtime exceções. Para obter mais informações, consulte [gerenciar exceções com o depurador](../debugger/managing-exceptions-with-the-debugger.md).

 Se você definir o depurador para interromper Common Language Runtime exceções, todas as exceções agora serão interrompidas no depurador, incluindo aquelas que você tratou e algumas exceções de primeira chance do próprio tempo de execução, o que pode não ser relevante para seu projeto. Erros que fazem referência a Msosec não podem ser encontrados aparecem em todos os projetos, mas são seguros para serem ignorados. Essas exceções Msosec não afetarão sua solução.

 Você também pode usar **try... Pegue** instruções sobre seus métodos para capturar exceções.

 Por padrão, o Visual Studio também não exibe erros de depuração Just-in-time para projetos do Office; no entanto, você pode habilitar esse recurso para que você possa ver os erros que são gerados. Para obter mais informações, consulte [depuração Just-in-time no Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Argumentos de linha de comando
 Se a **ação iniciar** na página de propriedades de **depuração** estiver definida como **Iniciar projeto**, o Visual Studio não usará argumentos de linha de comando ao depurar o projeto, mesmo que você tenha especificado argumentos de linha de comando como opções de início. Se você quiser usar argumentos de linha de comando ao iniciar a depuração, deverá selecionar uma **ação de início** diferente de **Iniciar projeto**.

## <a name="source-control"></a>Controle do código-fonte
 As propriedades de depuração não são compartilhadas entre vários usuários sob controle do código-fonte. Os projetos Visual Basic e C# armazenam as propriedades de depuração em um arquivo específico do usuário (*ProjectName*. vbproj. User ou *ProjectName*. csproj. User) e esse arquivo não está no controle do código-fonte. Se mais de uma pessoa estiver Depurando, cada pessoa deverá inserir as propriedades de depuração manualmente.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Depurar conjuntos de valores em cache em um projeto de nível de documento
 Toda vez que você cria um projeto, o conjunto de um é esvaziado e recriado. Se você quiser depurar um conjunto de armazenamento em cache, deverá abrir o documento fora do Visual Studio e, em seguida, anexar o depurador.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Depurar projetos de documento do Word com base no formato de documento do Word 97-2003 (*. doc)
 Para depurar um projeto de documento do Word com base no formato de documento do Word 97-2003 ( */* . doc *), você deve adicionar a pasta do projeto à lista de pastas confiáveis. Para obter mais informações sobre como fazer isso, consulte [conceder confiança a documentos](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Depurar suplementos desabilitados
 Microsoft Office aplicativos podem desabilitar os suplementos do VSTO que se comportam inesperadamente. Um aplicativo Microsoft Office desabilita os suplementos do VSTO para evitar que o código problemático seja carregado toda vez que o aplicativo for iniciado. No entanto, também é fácil causar um comportamento inesperado durante a depuração típica. Para obter informações sobre como reabilitar os suplementos do VSTO, consulte [como habilitar novamente um suplemento do VSTO que foi desabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).

 Há dois tipos de desabilitação que Microsoft Office aplicativos usam para suplementos do VSTO: desabilitação e desabilitação flexível.

### <a name="hard-disabling"></a>Desabilitação rígida
 A desabilitação forçada pode ocorrer quando um suplemento do VSTO faz com que o aplicativo seja fechado inesperadamente. Ele também pode ocorrer em seu computador de desenvolvimento se você parar o depurador enquanto o <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos em seu suplemento do VSTO estiver em execução. Quando um suplemento do VSTO é inativo, ele aparece na lista **itens desabilitados** no aplicativo.

 Se um aplicativo do Office desativar um suplemento do VSTO criado usando as ferramentas de desenvolvimento do Office no Visual Studio, o aplicativo desabilitará apenas o suplemento do VSTO que causou a falha. Outros suplementos do VSTO criados usando as ferramentas de desenvolvimento do Office no Visual Studio para o aplicativo do Office continuarão a ser carregados.

### <a name="soft-disabling"></a>Desabilitação flexível
 A desabilitação flexível pode ocorrer quando um suplemento do VSTO produz um erro que não faz com que o aplicativo feche inesperadamente. Por exemplo, um aplicativo pode desabilitar um suplemento do VSTO de maneira flexível se ele lançar uma exceção sem tratamento enquanto o <xref:Microsoft.Office.Tools.AddIn.Startup> manipulador de eventos estiver em execução. Quando um suplemento do VSTO é desabilitado de forma flexível, ele aparece na lista de **suplementos de aplicativos inativos** no aplicativo e o aplicativo altera o valor da entrada do registro **LoadBehavior** para o suplemento do VSTO para indicar que ele está descarregado. Para obter mais informações sobre a entrada do registro **LoadBehavior** , consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Solucionar erros de instalação usando o Visualizador de Eventos
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] grava mensagens no Visualizador de eventos no Windows para todas as exceções que são geradas quando você instala ou desinstala soluções do Office. Você pode usar essas mensagens para resolver problemas de instalação e implantação.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Solucionar problemas de erros de inicialização usando um arquivo de log e mensagens de erro
 O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] pode gravar todos os erros que ocorrem durante a inicialização em um arquivo de log ou exibir cada erro em uma caixa de mensagem. Por padrão, essas opções são desativadas. Você pode ativar as opções criando variáveis de ambiente.

 Para exibir cada erro em uma caixa de mensagem, crie uma variável de ambiente chamada `VSTO_SUPPRESSDISPLAYALERTS` e defina-a como 0 (zero). Você pode suprimir as mensagens excluindo a variável de ambiente ou definindo-a como 1 (uma).

 Para gravar os erros em um arquivo de log, crie uma variável de ambiente chamada `VSTO_LOGALERTS` e defina-a como 1 (uma). O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria o arquivo de log na pasta que contém o manifesto de implantação para o suplemento do VSTO ou na pasta que contém o documento ou planilha que está associado à personalização. Se isso falhar, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] criará o arquivo de log na pasta *% Temp%* local. Para suplementos do VSTO no nível de aplicativo, o nome padrão é *Add-in name*. vsto. log. Para projetos de nível de documento, o nome do arquivo de log é *nome do documento*. *extensão*. log, como ExcelWorkbook1.xlsx. log. Para interromper os erros de log, exclua a variável de ambiente ou defina-a como 0 (zero).

## <a name="see-also"></a>Confira também

- [Criar soluções do Office](../vsto/building-office-solutions.md)
- [Como: reabilitar um suplemento do VSTO que foi desabilitado](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)