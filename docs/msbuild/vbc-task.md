---
title: Tarefa Vbc | Microsoft Docs
ms.date: 04/12/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1710336ebc73be707e962733e37376b5689e10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631231"
---
# <a name="vbc-task"></a>tarefa Vbc

Envolve *vbc.exe*, que produz executáveis *(.exe),* bibliotecas de link dinâmico *(.dll)* ou módulos de código *(.netmodule).* Para obter mais informações sobre *vbc.exe,* consulte [o compilador de linha de comando Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index).

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `Vbc`.

| Parâmetro | Descrição |
|------------------------------| - |
| `AdditionalLibPaths` | Parâmetro `String[]` opcional.<br /><br /> Especifica as pastas adicionais nas quais procurar por assemblies especificados no atributo References. |
| `AddModules` | Parâmetro `String[]` opcional.<br /><br /> Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando. Este parâmetro corresponde ao interruptor [-addmodule](/dotnet/visual-basic/reference/command-line-compiler/addmodule) do compilador *vbc.exe.* |
| `BaseAddress` | Parâmetro `String` opcional.<br /><br /> Especifica o endereço básico do DLL. Este parâmetro corresponde ao interruptor [de endereço base](/dotnet/visual-basic/reference/command-line-compiler/baseaddress) do compilador *vbc.exe.* |
| `CodePage` | Parâmetro `Int32` opcional.<br /><br /> Especifica a página de código a ser usada para todos os arquivos de código-fonte na compilação. Este parâmetro corresponde ao interruptor [de página de código](/dotnet/visual-basic/reference/command-line-compiler/codepage) do compilador *vbc.exe.* |
| `DebugType` | Parâmetro `String[]` opcional.<br /><br /> Faz com que o compilador gere informações de depuração. Esse parâmetro pode ter os seguintes valores:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> O valor padrão é `full`, que permite anexar um depurador ao programa em execução. Um valor de `pdbonly` permite a depuração de código-fonte quando o programa é iniciado no depurador, mas exibe o código de linguagem assembly somente quando o programa em execução está anexado ao depurador. Para obter mais informações, consulte [-depuração (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `DefineConstants` | Parâmetro `String[]` opcional.<br /><br /> Define as constantes de compilador condicional. Os pares de símbolo/valor são separados por ponto e vírgula e são especificados usando a sintaxe a seguir:<br /><br /> *symbol1* `=` *value1* `;` *symbol2* `=` *value2*<br /><br /> Este parâmetro corresponde ao interruptor [-definir](/dotnet/visual-basic/reference/command-line-compiler/define) do compilador *vbc.exe.* |
| `DelaySign` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa colocará a chave pública no assembly. Se `false`, a tarefa assina totalmente o assembly. O valor padrão é `false`. Esse parâmetro não tem nenhum efeito a menos que usado com o parâmetro `KeyFile` ou `KeyContainer`. Este parâmetro corresponde ao interruptor [de sinal](/dotnet/visual-basic/reference/command-line-compiler/delaysign) de atraso do compilador *vbc.exe.* |
| `Deterministic` | Parâmetro `Boolean` opcional.<br/><br/> Se ele for `true`, fará com que o compilador gere um assembly cujo conteúdo binário é idêntico entre compilações caso as entradas sejam idênticas.<br/><br/>Para obter mais informações, confira [-deterministic](/dotnet/visual-basic/reference/command-line-compiler/deterministic). |
| `DisabledWarnings` | Parâmetro `String` opcional.<br /><br /> Suprime os avisos especificados. Você só precisa especificar a parte numérica do identificador de aviso. Vários avisos são separados por ponto e vírgula. Este parâmetro corresponde ao interruptor [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn) do compilador *vbc.exe.* |
| `DocumentationFile` | Parâmetro `String` opcional.<br /><br /> Processa os comentários de documentação para o arquivo XML especificado. Esse parâmetro substitui o atributo `GenerateDocumentation`. Para obter mais informações, consulte [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `EmitDebugInformation` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa gera informações de depuração e as coloca em um arquivo *.pdb.* Para obter mais informações, consulte [-depuração (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| `ErrorReport` | Parâmetro `String` opcional.<br /><br /> Especifica como a tarefa deve relatar erros do compilador interno. Esse parâmetro pode ter os seguintes valores:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Se `prompt` estiver especificado e ocorrer um erro interno do compilador, será exibida uma opção ao usuário para enviar os dados de erros à Microsoft.<br /><br /> Se `send` for especificado e ocorrer um erro interno do compilador, a tarefa enviará os dados de erros à Microsoft.<br /><br /> O valor padrão é `none`, que reporta os erros somente na saída de texto.<br /><br /> Este parâmetro corresponde ao interruptor [-errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport) do compilador *vbc.exe.* |
| `FileAlignment` | Parâmetro `Int32` opcional.<br /><br /> Especifica, em bytes, onde alinhar as seções do arquivo de saída. Esse parâmetro pode ter os seguintes valores:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Este parâmetro corresponde ao interruptor [-filealign](/dotnet/visual-basic/reference/command-line-compiler/filealign) do compilador *vbc.exe.* |
| `GenerateDocumentation` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, serão geradas informações sobre a documentação, que serão colocadas em um arquivo XML com o nome do arquivo executável ou da biblioteca que a tarefa está criando. Para obter mais informações, consulte [-doc](/dotnet/visual-basic/reference/command-line-compiler/doc). |
| `Imports` | Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Importa namespaces de coleções do item especificado. Este parâmetro corresponde ao interruptor [de importações](/dotnet/visual-basic/reference/command-line-compiler/imports) do compilador *vbc.exe.* |
| `KeyContainer` | Parâmetro `String` opcional.<br /><br /> Especifica o nome do contêiner da chave de criptografia. Esse parâmetro corresponde à opção [-keycontainer](/dotnet/visual-basic/reference/command-line-compiler/keycontainer) do compilador *vbc.exe*. |
| `KeyFile` | Parâmetro `String` opcional.<br /><br /> Especifica o nome de arquivo que contém a chave de criptografia. Para obter mais informações, consulte [-keyfile](/dotnet/visual-basic/reference/command-line-compiler/keyfile). |
| `LangVersion` | Parâmetro <xref:System.String?displayProperty=fullName> opcional.<br /><br /> Especifica a [versão da linguagem](/dotnet/visual-basic/language-reference/configure-language-version), como "15.5". |
| `LinkResources` | Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Cria um link para um recurso do .NET Framework no arquivo de saída; o arquivo de recurso não é colocado no arquivo de saída. Este parâmetro corresponde ao switch [-linkresource](/dotnet/visual-basic/reference/command-line-compiler/linkresource) do compilador *vbc.exe.* |
| `MainEntryPoint` | Parâmetro `String` opcional.<br /><br /> Especifica a classe ou o módulo que contém o procedimento `Sub Main`. Esse parâmetro corresponde à opção [-main](/dotnet/visual-basic/reference/command-line-compiler/main) do compilador *vbc.exe*. |
| `ModuleAssemblyName` | Parâmetro `String` opcional.<br /><br /> Especifica o assembly do qual esse módulo faz parte. |
| `NoConfig` | Parâmetro `Boolean` opcional.<br /><br /> Especifica que o compilador não deve usar o arquivo *vbc.rsp.* Este parâmetro corresponde ao parâmetro [-noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig) do compilador *vbc.exe.* |
| `NoLogo` | Parâmetro `Boolean` opcional.<br /><br /> Se for `true`, suprimirá a exibição de informações da barra de notificação do compilador. Este parâmetro corresponde ao interruptor [-nologo](/dotnet/visual-basic/reference/command-line-compiler/nologo) do compilador *vbc.exe.* |
| `NoStandardLib` | Parâmetro `Boolean` opcional.<br /><br /> Faz com que o compilador não referencie as bibliotecas padrão. Este parâmetro corresponde ao interruptor [-nostdlib](/dotnet/visual-basic/reference/command-line-compiler/nostdlib) do compilador *vbc.exe.* |
| `NoVBRuntimeReference` | Parâmetro `Boolean` opcional.<br /><br /> Somente para uso interno. Se for verdade, impede a referência automática ao *Microsoft.VisualBasic.dll*. |
| `NoWarnings` | Parâmetro `Boolean` opcional.<br /><br /> Se ele for `true`, a tarefa suprimirá todos os avisos. Para obter mais informações, consulte [-nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn). |
| `Optimize` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, habilita as otimizações do compilador. Este parâmetro corresponde ao interruptor [-otimizador](/dotnet/visual-basic/reference/command-line-compiler/optimize) do compilador *vbc.exe.* |
| `OptionCompare` | Parâmetro `String` opcional.<br /><br /> Especifica como são feitas comparações de cadeia de caracteres. Esse parâmetro pode ter os seguintes valores:<br /><br /> -   `binary`<br />-   `text`<br /><br /> O valor `binary` especifica que a tarefa usa comparações de cadeia de caracteres binária. O valor `text` especifica que a tarefa usa comparações de cadeia de caracteres de texto. O valor padrão desse parâmetro é `binary`. Este parâmetro corresponde ao interruptor [-optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare) do compilador *vbc.exe.* |
| `OptionExplicit` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a declaração explícita de variáveis é necessária. Este parâmetro corresponde ao interruptor [-optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit) do compilador *vbc.exe.* |
| `OptionInfer` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, permite a inferência de tipos de variáveis. |
| `OptionStrict` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa impõe semântica de tipo estrito para restringir conversões de tipo implícito. Este parâmetro corresponde ao interruptor [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) do compilador *vbc.exe.* |
| `OptionStrictType` | Parâmetro `String` opcional.<br /><br /> Especifica qual semântica de tipo estrito gera um aviso. Atualmente, há suporte para apenas "custom". Este parâmetro corresponde ao interruptor [-optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict) do compilador *vbc.exe.* |
| `OutputAssembly` | Parâmetro de saída `String` opcional.<br /><br /> Especifica o nome do arquivo de saída. Este parâmetro corresponde ao interruptor [de saída](/dotnet/visual-basic/reference/command-line-compiler/out) do compilador *vbc.exe.* |
| `Platform` | Parâmetro `String` opcional.<br /><br /> Especifica a plataforma do processador a ser direcionada pelo arquivo de saída. Esse parâmetro pode ter um valor igual a `x86`, `x64``Itanium` ou `anycpu`. O padrão é `anycpu`. Esse parâmetro corresponde à opção [-platform](/dotnet/visual-basic/reference/command-line-compiler/platform) do compilador *vbc.exe*. |
| `References` | Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Faz com que a tarefa importe informações de tipo público dos itens especificados para o projeto atual. Este parâmetro corresponde ao interruptor [de referência](/dotnet/visual-basic/reference/command-line-compiler/reference) do compilador *vbc.exe.* |
| `RemoveIntegerChecks` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, desabilita a verificação de erro de estouro de inteiro. O valor padrão é `false`. Esse parâmetro corresponde à opção [-removeintchecks](/dotnet/visual-basic/reference/command-line-compiler/removeintchecks) do compilador *vbc.exe*. |
| `Resources` | Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Insere um recurso do .NET Framework no arquivo de saída. Esse parâmetro corresponde à opção [-resource](/dotnet/visual-basic/reference/command-line-compiler/resource) do compilador *vbc.exe*. |
| `ResponseFiles` | Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica o arquivo de resposta que contém comandos para essa tarefa. Este parâmetro corresponde à opção [@ (Especificar Arquivo](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file) de resposta) do compilador *vbc.exe.* |
| `RootNamespace` | Parâmetro `String` opcional.<br /><br /> Especifica o namespace raiz para todas as declarações de tipo. Este parâmetro corresponde ao interruptor [-rootnamespace](/dotnet/visual-basic/reference/command-line-compiler/rootnamespace) do compilador *vbc.exe.* |
| `SdkPath` | Parâmetro `String` opcional.<br /><br /> Especifica a localização de *mscorlib.dll* e *microsoft.visualbasic.dll*. Esse parâmetro corresponde à opção [-sdkpath](/dotnet/visual-basic/reference/command-line-compiler/sdkpath) do compilador *vbc.exe*. |
| `Sources` | Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica um ou mais arquivos de origem do Visual Basic. |
| `TargetCompactFramework` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, a tarefa atingir o .NET Compact Framework. Este switch corresponde ao switch [-netcf](/dotnet/visual-basic/reference/command-line-compiler/netcf) do compilador *vbc.exe.* |
| `TargetType` | Parâmetro `String` opcional.<br /><br /> Especifica o formato do arquivo de saída. Esse parâmetro pode ter um valor igual a `library`, que cria uma biblioteca de códigos, `exe`, que cria um aplicativo de console, `module`, que cria um módulo ou `winexe`, que cria um programa do Windows. O padrão é `library`. Este parâmetro corresponde ao [interruptor-alvo](/dotnet/visual-basic/reference/command-line-compiler/target) do compilador *vbc.exe.* |
| `Timeout` | Parâmetro `Int32` opcional.<br /><br /> Especifica a quantidade de tempo em milissegundos após o qual o executável da tarefa é encerrado. O valor padrão é `Int.MaxValue`, indicando que não há período de tempo limite. |
| `ToolPath` | Parâmetro `String` opcional.<br /><br /> Especifica o local de onde a tarefa carregará o arquivo executável subjacente *(vbc.exe).* Se esse parâmetro não for especificado, a tarefa usará o caminho de instalação do SDK correspondente à versão da estrutura que está executando o MSBuild. |
| `TreatWarningsAsErrors` | Parâmetro `Boolean` opcional.<br /><br /> Se `true`, todos os avisos são tratados como erros. Para obter mais informações, consulte [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror). |
| `UseHostCompilerIfAvailable` | Parâmetro `Boolean` opcional.<br /><br /> Instrui a tarefa a usar o objeto do compilador em processo, se disponível. Usado somente pelo Visual Studio. |
| `Utf8Output` | Parâmetro `Boolean` opcional.<br /><br /> Registra a saída do compilador usando a codificação UTF-8. Este parâmetro corresponde ao interruptor [de saída -utf8](/dotnet/visual-basic/reference/command-line-compiler/utf8output) do compilador *vbc.exe.* |
| `Verbosity` | Parâmetro `String` opcional.<br /><br /> Especifica o nível de detalhes da saída do compilador. Os detalhes podem ser `Quiet`, `Normal` (o padrão) ou `Verbose`. |
| `WarningsAsErrors` | Parâmetro `String` opcional.<br /><br /> Especifica uma lista de avisos a serem tratados como erros. Para obter mais informações, consulte [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Esse parâmetro substitui o parâmetro `TreatWarningsAsErrors`. |
| `WarningsNotAsErrors` | Parâmetro `String` opcional.<br /><br /> Especifica uma lista de avisos que não são tratados como erros. Para obter mais informações, consulte [-warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror).<br /><br /> Esse parâmetro será útil apenas se o parâmetro `TreatWarningsAsErrors` for definido como `true`. |
| `Win32Icon` | Parâmetro `String` opcional.<br /><br /> Insere um arquivo *.ico* no conjunto, o que dá ao arquivo de saída a aparência desejada no **File Explorer**. Este parâmetro corresponde ao interruptor [-win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon) do compilador *vbc.exe.* |
| `Win32Resources` | Parâmetro `String` opcional.<br /><br /> Insere um arquivo de recurso Win32 *(.res)* no arquivo de saída. Este parâmetro corresponde ao switch [-win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource) do compilador *vbc.exe.* |

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.ToolTask>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo a seguir compila um projeto do Visual Basic.

```xml
<VBC
   Sources="@(sources)"
   Resources="strings.resources"
   Optimize="true"
   OutputAssembly="out.exe"/>
```

## <a name="see-also"></a>Confira também

- [Compilador de linha de comando Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
