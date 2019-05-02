---
title: Opções de linha de comando do Devenv
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- switches, Devenv
- command-line switches, Devenv
- command line [Visual Studio], switches
- Devenv
ms.assetid: e12bc6ed-74fd-4bea-8d7c-89b99c20bad8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db9aaeb48095b058abb0deefa342598eefeed1b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970210"
---
# <a name="devenv-command-line-switches"></a>Opções de linha de comando do Devenv

O Devenv permite definir várias opções no IDE, compilar, depurar e implantar projetos a partir de uma linha de comando. Use essas opções para executar o IDE com um script ou arquivo .bat (por exemplo, um script de nightly build) ou para iniciar o IDE em uma configuração específica.

> [!NOTE]
> Para tarefas relacionadas ao build, é recomendável usar o MSBuild em vez do Devenv. Para obter mais informações, consulte [Referência de linha de comando do MSBuild](../../msbuild/msbuild-command-line-reference.md).

Para saber mais sobre as opções relacionadas ao desenvolvimento do VSPackage, consulte [Opções de linha de comando do Devenv para desenvolvimento de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md).

## <a name="devenv-switch-syntax"></a>Sintaxe da opção do devenv

Os comandos que começam com `devenv` são manipuladas pelo utilitário do `devenv.com`, que fornece a saída por meio de fluxos de sistema padrão, como `stdout` e `stderr`. O utilitário determina o redirecionamento de E/S apropriado quando ele captura a saída, por exemplo, em um arquivo .txt.

Como alternativa, os comandos que começam com `devenv.exe` podem usar as mesmas opções, mas o utilitário `devenv.com` é ignorado. Usando `devenv.exe` diretamente impede que a saída seja exibida no console.

As regras de sintaxe para opções do `devenv` são semelhantes às regras de outros utilitários de linha de comando do DOS. As regras de sintaxe a seguir se aplicam a todas as opções `devenv` e seus argumentos:

- Os comandos começam com `devenv`.

- As opções não diferenciam maiúsculas de minúsculas.

- Você pode especificar uma opção usando um hífen (-) ou uma barra (/).

- Ao especificar uma solução ou um projeto, o primeiro argumento é o nome do arquivo de solução ou do arquivo de projeto, incluindo o caminho do arquivo.

- Se o primeiro argumento for um arquivo que não seja uma solução ou um projeto, esse arquivo será aberto no editor apropriado, em uma nova instância do IDE.

- Ao fornecer um nome de arquivo de projeto em vez de um nome de arquivo de solução, um comando `devenv` pesquisa na pasta pai do arquivo de projeto um arquivo de solução que tem o mesmo nome. Por exemplo, o comando `devenv myproject1.vbproj /build` pesquisa um arquivo de solução chamado `myproject1.sln` na pasta pai.

  > [!NOTE]
  > Apenas um arquivo de solução que referencia esse projeto deve ser localizado em sua pasta pai. Se a pasta pai não contiver nenhum arquivo de solução que referencie esse projeto ou se contiver dois ou mais arquivos de solução que a referenciem, então um arquivo de solução temporário será criado.

- Quando nomes de arquivo e caminhos de arquivo incluírem espaços, será necessário usar aspas duplas (""). Por exemplo, `"c:\project a\"`.

- Insira um caractere de espaço entre as opções e os argumentos na mesma linha. Por exemplo, o comando `devenv /log output.txt` abre o IDE e coloca todas as informações de log dessa sessão em output.txt.

- Não é possível usar sintaxe de correspondência de padrões em comandos do `devenv`.

## <a name="devenv-switches"></a>Opções do devenv

As seguintes opções de linha de comando apresentam o IDE e realizam a tarefa descrita.

|Opção de linha de comando|Descrição|
| - |-----------------|
|[/Command](command-devenv-exe.md)|Inicia o IDE e executa o comando especificado.<br /><br /> `devenv /command "nav https://docs.microsoft.com/"`|
|[/DebugExe](debugexe-devenv-exe.md)|Carrega um executável C++ no controle do depurador. Esta opção não está disponível nos executáveis do Visual Basic ou C#. Para obter mais informações, consulte [Automatically start a process in the debugger (Iniciar automaticamente um processo no depurador)](../../debugger/debug-multiple-processes.md#BKMK_Automatically_start_an_process_in_the_debugger).<br /><br /> `devenv /debugexe mysln.exe`|
|[/Diff](diff.md)|Compara dois arquivos. Usa quatro parâmetros: *SourceFile*, *TargetFile*, *SourceDisplayName* (opcional) e *TargetDisplayName* (opcional).<br /><br /> `devenv /diff File1 File2 Alias1 Alias2`|
|[/DoNotLoadProjects](donotloadprojects-devenv-exe.md)|Abre a solução especificada sem carregar projetos.<br /><br /> `devenv /donotloadprojects mysln.sln`|
|[/Edit](edit-devenv-exe.md)|Abre os arquivos especificados em uma instância em execução deste aplicativo. Se não houver nenhuma instância em execução, uma nova instância será iniciada com um layout de janela simplificado.<br /><br /> `devenv /edit File1 File2`|
|[/LCID ou /L](lcid-devenv-exe.md)|Define o idioma padrão do IDE. Se a linguagem especificada não estiver incluída em sua instalação do Visual Studio, essa configuração será ignorada.<br /><br /> `devenv /l 1033`|
|[/Log](log-devenv-exe.md)|Inicia o Visual Studio e registra toda a atividade no arquivo de log.<br /><br /> `devenv /log mylogfile.xml`|
|[/NoSplash](nosplash-devenv-exe.md)|Abre o IDE sem mostrar a tela inicial.<br /><br /> `devenv /nosplash File1 File2`|
|[/Run ou /R](run-devenv-exe.md)|Compila e executa a solução especificada.<br /><br /> `devenv /run mysln.sln`|
|[/RunExit](runexit-devenv-exe.md)|Compila e executa a solução especificada, minimiza o IDE quando a solução é executada e fecha o IDE depois que a solução termina a execução.<br /><br /> `devenv /runexit mysln.sln`|
|[/SafeMode](safemode-devenv-exe.md)|Inicia o Visual Studio no modo de segurança. Esta opção carrega somente o ambiente padrão, os serviços padrão e as versões enviadas de pacotes de terceiros.<br /><br /> Esta opção não aceita nenhum argumento.|
|[/UseEnv](useenv-devenv-exe.md)|Faz com que o IDE use variáveis de ambiente PATH, INCLUDE, LIBPATH e LIB para a compilação C++. Essa opção é instalada com a carga de trabalho de **Desenvolvimento para desktop com C++**. Para obter mais informações, consulte [Configurando o caminho e variáveis de ambiente para Builds de linha de comando](/cpp/build/setting-the-path-and-environment-variables-for-command-line-builds).|

As opções de linha de comando a seguir não exibem o IDE.

|Opção de linha de comando|Descrição|
| - |-----------------|
|[/?](q-devenv-exe.md)|Exibe a ajuda para as opções do `devenv` na **janela do prompt de comando**.<br /><br /> Esta opção não aceita nenhum argumento.|
|[/Build](build-devenv-exe.md)|Cria a solução ou o projeto especificado de acordo com a configuração da solução especificada.<br /><br /> `devenv mysln.sln /build`|
|[/Clean](clean-devenv-exe.md)|Exclui os arquivos criados pelo comando de build sem afetar os arquivos de origem.<br /><br /> `devenv mysln.sln /clean`|
|[/Deploy](deploy-devenv-exe.md)|Compila a solução com os arquivos necessários para implantação, de acordo com a configuração da solução.<br /><br /> `devenv mysln.sln /deploy`|
|[/Out](out-devenv-exe.md)|Permite que você especifique um arquivo para receber erros ao compilar.<br /><br /> `devenv mysln.sln /build Debug /out log.txt`|
|[/Project](project-devenv-exe.md)|O projeto a ser criado, limpo ou implantado. É possível usar esta opção somente se você tiver fornecido a opção `/Build`, `/Rebuild`, `/Clean` ou `/Deploy`.<br /><br /> `devenv mysln.sln /build Debug /project proj1`|
|[/ProjectConfig](projectconfig-devenv-exe.md)|Especifica a configuração de projeto a ser criada ou implantada. É possível usar esta opção somente se você tiver fornecido a opção `/Project`.<br /><br /> `devenv mysln.sln /build Release /project proj1 /projectconfig Release`|
|[/Rebuild](rebuild-devenv-exe.md)|Limpa e depois compila a solução ou o projeto especificado de acordo com a configuração da solução especificada.<br /><br /> `devenv mysln.sln /rebuild`|
|[/ResetSettings](resetsettings-devenv-exe.md)|Restaura as configurações padrão do Visual Studio. Opcionalmente, redefine as configurações para o arquivo `.vssettings` especificado.<br /><br /> `devenv /resetsettings mysettings.vssettings`|
|[/Upgrade](upgrade-devenv-exe.md)|Atualiza o arquivo de solução especificado e todos os seus arquivos de projeto ou o arquivo de projeto especificado, para os formatos do Visual Studio atuais para esses arquivos.<br /><br /> `devenv mysln.sln /upgrade`|

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](general-environment-options-dialog-box.md)
- [Opções de linha de comando do Devenv para desenvolvimento de VSPackage](../../extensibility/devenv-command-line-switches-for-vspackage-development.md)
