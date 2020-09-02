---
title: Referência da Tarefa do MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbec3c7c020bae0e94bc16bdb1fe9740a36a93ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78865317"
---
# <a name="msbuild-task-reference"></a>Referência de tarefas do MSBuild

Tarefas fornecem o código que é executado durante o processo de build. As tarefas na lista a seguir são incluídas no MSBuild. Quando a carga de trabalho do C++ é instalada, são disponibilizadas tarefas adicionais que são usadas para criar projetos em C++. Para obter mais informações, consulte [tarefas do C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Além dos parâmetros listados nos tópicos nesta seção, cada tarefa também tem os parâmetros a seguir:

| Parâmetro | Descrição |
|-------------------| - |
| `Condition` | Parâmetro `String` opcional.<br /><br /> Uma `Boolean` expressão que o mecanismo MSBuild usa para determinar se esta tarefa será executada. Para obter informações sobre as condições com suporte pelo MSBuild, consulte [condições](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parâmetro opcional. Pode conter um dos seguintes valores:<br /><br /> -   **WarnAndContinue** ou **true**. Quando uma tarefa falha, as tarefas subsequentes no elemento de [destino](../msbuild/target-element-msbuild.md) e a compilação continuam a ser executadas, e todos os erros da tarefa são tratados como avisos.<br />-   **ErrorAndContinue**. Quando uma tarefa falha, as tarefas subsequentes no elemento de `Target` e o build continuam em execução e todos os erros da tarefa são tratados como erros.<br />-   **ErrorAndStop** ou **false** (padrão). Quando uma tarefa falha, as tarefas restantes do elemento de `Target` e o build não são executadas e todo o elemento de `Target` e o build são considerados como em falha.<br /><br /> As versões do .NET Framework antes da 4.5 ofereciam suporte somente aos valores `true` e `false`.<br /><br /> Para obter mais informações, consulte [como ignorar erros em tarefas](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Nesta seção

- [Classe base Task](../msbuild/task-base-class.md)

 Adiciona vários parâmetros para as tarefas que derivam da classe <xref:Microsoft.Build.Utilities.Task>. Não se destina a ser usado diretamente.

- [Classe base TaskExtension](../msbuild/taskextension-base-class.md)

 Adiciona vários parâmetros para as tarefas que derivam da classe <xref:Microsoft.Build.Tasks.TaskExtension>. Não se destina a ser usado diretamente.

- [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Adiciona vários parâmetros para as tarefas que derivam da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Não se destina a ser usado diretamente.

- [Tarefa AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)

 Cria um assembly com um manifesto com base em um ou mais arquivos que são arquivos de recurso ou módulos.

- [Tarefa AspNetCompiler](../msbuild/aspnetcompiler-task.md)

 Encapsula *aspnet_compiler.exe*, um utilitário para pré-compilar aplicativos ASP.NET.

- [Tarefa AssignCulture](../msbuild/assignculture-task.md)

 Atribui os identificadores de cultura a itens.

- [Tarefa AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)

 Aceita uma lista de cadeias de caracteres de configuração e as atribui a projetos especificados.

- [Tarefa AssignTargetPath](../msbuild/assigntargetpath-task.md)

 Aceita uma lista de arquivos e adiciona atributos `<TargetPath>` se eles ainda não foram especificados.

- [Tarefa CallTarget](../msbuild/calltarget-task.md)

 Invoca um destino no arquivo de projeto.

- [Tarefa CombinePath](../msbuild/combinepath-task.md)

 Combina os caminhos especificados em um único caminho.

- [Tarefa ConvertToAbsolutePath](../msbuild/converttoabsolutepath-task.md)

 Converte uma referência ou caminho relativo em um caminho absoluto.

- [tarefa Copy](../msbuild/copy-task.md)

 Copia os arquivos para um novo local.

- [Tarefa CreateCSharpManifestResourceName](../msbuild/createcsharpmanifestresourcename-task.md)

 Cria um nome de manifesto em estilo C# a partir de um determinado nome de arquivo *. resx* ou outro recurso.

- [Tarefa CreateItem](../msbuild/createitem-task.md)

 Popula as coleções de itens dos itens de entrada, permitindo que os itens sejam copiados de uma lista para outra.

- [Tarefa CreateProperty](../msbuild/createproperty-task.md)

 Popula as propriedades de valores de entrada, permitindo que os valores sejam copiados de uma propriedade ou cadeia de caracteres para outra.

- [Tarefa CreateVisualBasicManifestResourceName](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Cria um nome de manifesto estilo Visual Basic a partir de um determinado nome de arquivo *. resx* ou outro recurso.

- [tarefa Csc](../msbuild/csc-task.md)

 Chama o Compilador do Visual C# para produzir arquivos executáveis, bibliotecas de vínculo dinâmico ou módulos de código.

- [tarefa Delete](../msbuild/delete-task.md)

 Exclui os arquivos especificados.

- [Tarefa DownloadFile](../msbuild/downloadfile-task.md)

 Baixa um arquivo no local especificado.

- [tarefa Error](../msbuild/error-task.md)

 Interrompe um build e registra um erro com base em uma instrução condicional avaliada.

- [tarefa Exec](../msbuild/exec-task.md)

 Executa o programa ou comando especificado com os argumentos especificados.

- [Tarefa FindAppConfigFile](../msbuild/findappconfigfile-task.md)

 Localiza o arquivo *app.config*, caso haja algum, nas listas fornecidas.

- [Tarefa FindInList](../msbuild/findinlist-task.md)

 Localiza um item em uma lista especificada com o itemspec correspondente.

- [Tarefa FindUnderPath](../msbuild/findunderpath-task.md)

 Determina quais itens na coleção de itens especificados existem na pasta especificada ou suas subpastas.

- [Tarefa FormatUrl](../msbuild/formaturl-task.md)

 Converte uma URL em um formato de URL correto.

- [Tarefa FormatVersion](../msbuild/formatversion-task.md)

 Acrescenta o número de revisão ao número de versão.

- [Tarefa GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md)

 Gera um manifesto de aplicativo ClickOnce ou um manifesto nativo.

- [Tarefa GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)

 Fornece uma forma automatizada de detectar, baixar e instalar um aplicativo e seus pré-requisitos.

- [Tarefa GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)

 Gera um manifesto de implantação do ClickOnce.

- [Tarefa GenerateResource](../msbuild/generateresource-task.md)

 Converte arquivos *.txt* e *.resx* em arquivos *.resources* binários do Common Language Runtime.

- [Tarefa GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)

 Gera a confiança do aplicativo do manifesto base e dos parâmetros `TargetZone` e `ExcludedPermissions`.

- [Tarefa GetAssemblyIdentity](../msbuild/getassemblyidentity-task.md)

 Recupera as identidades do assembly dos arquivos especificados e gera como saída as informações de identidade.

- [Tarefa GetFileHash](../msbuild/getfilehash-task.md)

 Calcula as somas de verificação do conteúdo de um arquivo ou conjunto de arquivos.

- [Tarefa GetFrameworkPath](../msbuild/getframeworkpath-task.md)

 Recupera o caminho para os assemblies .NET Framework.

- [Tarefa GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)

 Recupera o caminho para o SDK (Software Development Kit) do Windows.

- [Tarefa GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)

 Retorna os caminhos do assembly de referência de diversas estruturas.

- [tarefa LC](../msbuild/lc-task.md)

 Gera um arquivo *.license* de um arquivo *.licx*.

- [Tarefa MakeDir](../msbuild/makedir-task.md)

 Cria diretórios e, se necessário, qualquer diretório pai.

- [tarefa de mensagem](../msbuild/message-task.md)

 Registra uma mensagem durante a compilação.

- [tarefa Move](../msbuild/move-task.md)

 Move os arquivos para um novo local.

- [tarefa MSBuild](../msbuild/msbuild-task.md)

 Cria projetos do MSBuild de outro projeto do MSBuild.

- [Tarefa ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)

 Lê uma lista de itens de um arquivo de texto.

- [Tarefa RegisterAssembly](../msbuild/registerassembly-task.md)

 Lê os metadados dentro do assembly especificado e adiciona as entradas necessárias ao Registro.

- [Tarefa RemoveDir](../msbuild/removedir-task.md)

 Remove os diretórios especificados e todos os seus arquivos e subdiretórios.

- [Tarefa RemoveDuplicates](../msbuild/removeduplicates-task.md)

 Remove itens duplicados da coleção do item especificado.

- [Tarefa RequiresFramework35SP1Assembly](../msbuild/requiresframework35sp1assembly-task.md)

 Determina se o aplicativo requer o .NET Framework 3.5 SP1.

- Tarefa ResGen

 Obsoleto. Use a [Tarefa GenerateResource](../msbuild/generateresource-task.md) para converter arquivos *.txt* e *.resx* em arquivos *.resources* binários do Common Language Runtime.

- [Tarefa ResolveAssemblyReference](../msbuild/resolveassemblyreference-task.md)

 Determina todos os assemblies que dependem dos assemblies especificados.

- [Tarefa ResolveComReference](../msbuild/resolvecomreference-task.md)

 Usa uma lista de um ou mais nomes de biblioteca de tipos ou arquivos *. tlb* e resolve essas bibliotecas de tipos para locais no disco.

- [Tarefa ResolveKeySource](../msbuild/resolvekeysource-task.md)

 Determina a origem da chave de nome forte

- [Tarefa ResolveManifestFiles](../msbuild/resolvemanifestfiles-task.md)

 Resolve os seguintes itens no processo de build para arquivos de geração de manifesto: itens compilados, dependências, satélites, conteúdo, símbolos de depuração e documentação.

- [Tarefa ResolveNativeReference](../msbuild/resolvenativereference-task.md)

 Resolve referências nativas.

- [Tarefa ResolveNonMSBuildProjectOutput](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Determina os arquivos de saída para referências de projeto não MSBuild.

- [tarefa SGen](../msbuild/sgen-task.md)

 Cria um assembly de serialização de XML para tipos no assembly especificado.

- [Tarefa SignFile](../msbuild/signfile-task.md)

 Assina o arquivo especificado usando o certificado especificado.

- [tarefa Touch](../msbuild/touch-task.md)

 Define os horários de modificação e acesso aos arquivos.

- [Tarefa UnregisterAssembly](../msbuild/unregisterassembly-task.md)

 Cancela o registro os assemblies especificados para fins de interoperabilidade COM.

- [Tarefa de descompactação](../msbuild/unzip-task.md)

 Descompacta um arquivo *.zip* no local especificado.

- [Tarefa UpdateManifest](../msbuild/updatemanifest-task.md)

 Atualiza as propriedades selecionadas em um manifesto e assina-as novamente.

- [tarefa Vbc](../msbuild/vbc-task.md)

 Invoca o compilador do Visual Basic para produzir arquivos executáveis, bibliotecas de vínculo dinâmico ou módulos de código.

- [Tarefa VerifyFileHash](../msbuild/verifyfilehash-task.md)

 Verifica se um arquivo corresponde ao hash do arquivo esperado.

- [tarefa Warning](../msbuild/warning-task.md)

 Registra um aviso durante um build com base em uma instrução condicional avaliada.

- [Tarefa WriteCodeFragment](../msbuild/writecodefragment-task.md)

 Gera um arquivo de código temporário pelo uso do fragmento de código gerado especificado. Não exclui o arquivo.

- [Tarefa WriteLinesToFile](../msbuild/writelinestofile-task.md)

 Grava os itens especificados no arquivo de texto especificado.

- [Tarefa XmlPeek](../msbuild/xmlpeek-task.md)

 Retorna os valores conforme especificado por uma consulta de XPath em um arquivo XML.

- [Tarefa XmlPoke](../msbuild/xmlpoke-task.md)

 Define os valores conforme especificado por uma consulta de XPath em um arquivo XML.

- [Tarefa XslTransformation](../msbuild/xsltransformation-task.md)

 Transformações um XML de entrada usando um *XSLT (linguagem XSL Transformation)* ou XSLT compilado e saídas para um arquivo ou um dispositivo de saída.

- [Tarefa ZipDirectory](../msbuild/zipdirectory-task.md)

 Cria um arquivo *.zip* do conteúdo de um diretório.

## <a name="see-also"></a>Confira também

- [Referência do MSBuild](../msbuild/msbuild-reference.md)
- [Produção de tarefas](../msbuild/task-writing.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
