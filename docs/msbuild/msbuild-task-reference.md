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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865317"
---
# <a name="msbuild-task-reference"></a>Referência de tarefas do MSBuild

Tarefas fornecem o código que é executado durante o processo de build. As tarefas na lista a seguir estão incluídas no MSBuild. Quando a carga de trabalho C++ é instalada, estão disponíveis tarefas adicionais que são usadas para construir projetos C++. Para obter mais informações, consulte [as tarefas C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Além dos parâmetros listados nos tópicos nesta seção, cada tarefa também tem os parâmetros a seguir:

| Parâmetro | Descrição |
|-------------------| - |
| `Condition` | Parâmetro `String` opcional.<br /><br /> Uma `Boolean` expressão que o mecanismo MSBuild usa para determinar se essa tarefa será executada. Para obter informações sobre as condições suportadas pelo MSBuild, consulte [Condições](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Parâmetro opcional. Pode conter um dos seguintes valores:<br /><br /> -   **WarnAndContinue** ou **true**. Quando uma tarefa falha, as tarefas subseqüentes no elemento [Destino](../msbuild/target-element-msbuild.md) e na compilação continuam a ser executadas, e todos os erros da tarefa são tratados como avisos.<br />-   **ErrorAndContinue**. Quando uma tarefa falha, as tarefas subsequentes no elemento de `Target` e o build continuam em execução e todos os erros da tarefa são tratados como erros.<br />-   **ErrorAndStop** ou **false** (padrão). Quando uma tarefa falha, as tarefas restantes do elemento de `Target` e o build não são executadas e todo o elemento de `Target` e o build são considerados como em falha.<br /><br /> As versões do .NET Framework antes da 4.5 ofereciam suporte somente aos valores `true` e `false`.<br /><br /> Para obter mais informações, consulte [Como: Ignorar erros nas tarefas](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>Nesta seção

- [Classe base de tarefas](../msbuild/task-base-class.md)

 Adiciona vários parâmetros para as tarefas que derivam da classe <xref:Microsoft.Build.Utilities.Task>. Não se destina a ser usado diretamente.

- [Classe base de extensão de tarefas](../msbuild/taskextension-base-class.md)

 Adiciona vários parâmetros para as tarefas que derivam da classe <xref:Microsoft.Build.Tasks.TaskExtension>. Não se destina a ser usado diretamente.

- [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Adiciona vários parâmetros para as tarefas que derivam da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Não se destina a ser usado diretamente.

- [Tarefa AL (Assembly Linker)](../msbuild/al-assembly-linker-task.md)

 Cria um assembly com um manifesto com base em um ou mais arquivos que são arquivos de recurso ou módulos.

- [Tarefa AspNetCompiler](../msbuild/aspnetcompiler-task.md)

 Encapsula *aspnet_compiler.exe*, um utilitário para pré-compilar aplicativos ASP.NET.

- [Tarefa AtribuirCultura](../msbuild/assignculture-task.md)

 Atribui os identificadores de cultura a itens.

- [AtribuiratribuiatarefaConfiguração de configuração](../msbuild/assignprojectconfiguration-task.md)

 Aceita uma lista de cadeias de caracteres de configuração e as atribui a projetos especificados.

- [Tarefa AssignTargetPath](../msbuild/assigntargetpath-task.md)

 Aceita uma lista de arquivos e adiciona atributos `<TargetPath>` se eles ainda não foram especificados.

- [Tarefa CallTarget](../msbuild/calltarget-task.md)

 Invoca um destino no arquivo de projeto.

- [Tarefa CombinePath](../msbuild/combinepath-task.md)

 Combina os caminhos especificados em um único caminho.

- [ConvertToAbsolutePath task](../msbuild/converttoabsolutepath-task.md)

 Converte uma referência ou caminho relativo em um caminho absoluto.

- [Tarefa de copiar](../msbuild/copy-task.md)

 Copia os arquivos para um novo local.

- [CriarcSharpManifestRecurso-chefe](../msbuild/createcsharpmanifestresourcename-task.md)

 Cria um nome manifesto de estilo C#a partir de um nome de arquivo *.resx* ou outro recurso.

- [Tarefa CriarItem](../msbuild/createitem-task.md)

 Popula as coleções de itens dos itens de entrada, permitindo que os itens sejam copiados de uma lista para outra.

- [Tarefa CreateProperty](../msbuild/createproperty-task.md)

 Popula as propriedades de valores de entrada, permitindo que os valores sejam copiados de uma propriedade ou cadeia de caracteres para outra.

- [CriaratarefadeCriaçãoBásicaManifestResourceName task](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Cria um nome manifesto de estilo Visual Basic a partir de um nome de arquivo *.resx* ou outro recurso.

- [Tarefa csc](../msbuild/csc-task.md)

 Chama o Compilador do Visual C# para produzir arquivos executáveis, bibliotecas de vínculo dinâmico ou módulos de código.

- [Excluir tarefa](../msbuild/delete-task.md)

 Exclui os arquivos especificados.

- [DownloadTarefaArquivo](../msbuild/downloadfile-task.md)

 Baixa um arquivo no local especificado.

- [tarefa Error](../msbuild/error-task.md)

 Interrompe um build e registra um erro com base em uma instrução condicional avaliada.

- [Tarefa executiva](../msbuild/exec-task.md)

 Executa o programa ou comando especificado com os argumentos especificados.

- [FindAppConfigFile task](../msbuild/findappconfigfile-task.md)

 Localiza o arquivo *app.config*, caso haja algum, nas listas fornecidas.

- [Tarefa FindInList](../msbuild/findinlist-task.md)

 Localiza um item em uma lista especificada com o itemspec correspondente.

- [Tarefa FindUnderPath](../msbuild/findunderpath-task.md)

 Determina quais itens na coleção de itens especificados existem na pasta especificada ou suas subpastas.

- [Tarefa FormatUrl](../msbuild/formaturl-task.md)

 Converte uma URL em um formato de URL correto.

- [Tarefa FormatVersion](../msbuild/formatversion-task.md)

 Acrescenta o número de revisão ao número de versão.

- [Gerara tarefaDo'sODeSo do ApplicationManifest](../msbuild/generateapplicationmanifest-task.md)

 Gera um manifesto de aplicativo ClickOnce ou um manifesto nativo.

- [Tarefa GenerateBootstrapper](../msbuild/generatebootstrapper-task.md)

 Fornece uma forma automatizada de detectar, baixar e instalar um aplicativo e seus pré-requisitos.

- [Tarefa GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)

 Gera um manifesto de implantação do ClickOnce.

- [Tarefa GenerateResource](../msbuild/generateresource-task.md)

 Converte arquivos *.txt* e *.resx* em arquivos *.resources* binários do Common Language Runtime.

- [Tarefa GenerateTrustInfo](../msbuild/generatetrustinfo-task.md)

 Gera a confiança do aplicativo do manifesto base e dos parâmetros `TargetZone` e `ExcludedPermissions`.

- [ObtertarefaDeidentidade do GetAssembly](../msbuild/getassemblyidentity-task.md)

 Recupera as identidades do assembly dos arquivos especificados e gera como saída as informações de identidade.

- [Tarefa GetFileHash](../msbuild/getfilehash-task.md)

 Calcula as somas de verificação do conteúdo de um arquivo ou conjunto de arquivos.

- [Tarefa GetFrameworkPath](../msbuild/getframeworkpath-task.md)

 Recupera o caminho para os assemblies .NET Framework.

- [Tarefa GetFrameworkSdkPath](../msbuild/getframeworksdkpath-task.md)

 Recupera o caminho para o Windows Software Development Kit (SDK).

- [Tarefa GetReference'SPaths](../msbuild/getreferenceassemblypaths-task.md)

 Retorna os caminhos do assembly de referência de diversas estruturas.

- [tarefa LC](../msbuild/lc-task.md)

 Gera um arquivo *.license* de um arquivo *.licx*.

- [Faça tarefa de Dir](../msbuild/makedir-task.md)

 Cria diretórios e, se necessário, qualquer diretório pai.

- [Tarefa de mensagem](../msbuild/message-task.md)

 Registra uma mensagem durante a compilação.

- [tarefa Move](../msbuild/move-task.md)

 Move os arquivos para um novo local.

- [tarefa MSBuild](../msbuild/msbuild-task.md)

 Constrói projetos msbuild a partir de outro projeto MSBuild.

- [Tarefa ReadLinesFromFile](../msbuild/readlinesfromfile-task.md)

 Lê uma lista de itens de um arquivo de texto.

- [RegistrartarefaTarefaAssembly](../msbuild/registerassembly-task.md)

 Lê os metadados dentro do assembly especificado e adiciona as entradas necessárias ao Registro.

- [Remover tarefa Dir](../msbuild/removedir-task.md)

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

 Pega uma lista de um ou mais nomes de biblioteca de tipo ou arquivos *.tlb* e resolve essas bibliotecas de tipo para locais em disco.

- [Tarefa ResolveKeySource](../msbuild/resolvekeysource-task.md)

 Determina a origem da chave de nome forte

- [Resolvera tarefaManifestFiles](../msbuild/resolvemanifestfiles-task.md)

 Resolve os seguintes itens no processo de build para arquivos de geração de manifesto: itens compilados, dependências, satélites, conteúdo, símbolos de depuração e documentação.

- [Tarefa ResolveNativeReference](../msbuild/resolvenativereference-task.md)

 Resolve referências nativas.

- [Tarefa ResolveNonMSBuildProjectMissão de saída](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Determina os arquivos de saída para referências de projeto não MSBuild.

- [Tarefa SGen](../msbuild/sgen-task.md)

 Cria um assembly de serialização de XML para tipos no assembly especificado.

- [Tarefa SignFile](../msbuild/signfile-task.md)

 Assina o arquivo especificado usando o certificado especificado.

- [Tarefa de toque](../msbuild/touch-task.md)

 Define os horários de modificação e acesso aos arquivos.

- [Tarefa DesregistrarMontagem](../msbuild/unregisterassembly-task.md)

 Cancela o registro os assemblies especificados para fins de interoperabilidade COM.

- [Tarefa unzip](../msbuild/unzip-task.md)

 Descompacta um arquivo *.zip* no local especificado.

- [Tarefa UpdateManifest](../msbuild/updatemanifest-task.md)

 Atualiza as propriedades selecionadas em um manifesto e assina-as novamente.

- [Tarefa VBC](../msbuild/vbc-task.md)

 Invoca o compilador do Visual Basic para produzir arquivos executáveis, bibliotecas de vínculo dinâmico ou módulos de código.

- [Tarefa VerifyFileHash](../msbuild/verifyfilehash-task.md)

 Verifica se um arquivo corresponde ao hash do arquivo esperado.

- [Tarefa de aviso](../msbuild/warning-task.md)

 Registra um aviso durante um build com base em uma instrução condicional avaliada.

- [Tarefa 'Gravar'' WriteCodeFragment](../msbuild/writecodefragment-task.md)

 Gera um arquivo de código temporário pelo uso do fragmento de código gerado especificado. Não exclui o arquivo.

- [Tarefa 'Write'S'sFile'](../msbuild/writelinestofile-task.md)

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
- [Redação de tarefas](../msbuild/task-writing.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
