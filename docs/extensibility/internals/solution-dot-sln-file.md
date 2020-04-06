---
title: Solução (. SLn) arquivo
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705324"
---
# <a name="solution-sln-file"></a>Arquivo de solução (.sln)

Uma solução é uma estrutura para organização de projetos no Visual Studio. A solução mantém as informações do estado para projetos em dois arquivos:

- .sln arquivo (baseado em texto, compartilhado)

- Arquivo .suo (opções de solução binárias e específicas do usuário)

Para obter mais informações sobre arquivos .suo, consulte [Opções de usuário da solução (. Suo) Arquivo](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Se o vsPackage for carregado como resultado de ser referenciado no arquivo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> .sln, o ambiente será lido no arquivo .sln.

O arquivo .sln contém informações baseadas em texto que o ambiente usa para encontrar e carregar os parâmetros de valor de nome para os dados persistidos e o projeto VSPackages que ele faz referência. Quando um usuário abre uma solução, `preSolution`o `Project`ambiente `postSolution` circula através do , e informações no arquivo .sln para carregar a solução, projetos dentro da solução e quaisquer informações persistindo anexadas à solução.

Cada arquivo do projeto contém informações adicionais lidas pelo ambiente para preencher a hierarquia com os itens desse projeto. A persistência de dados hierárquicos é controlada pelo projeto. Os dados normalmente não são armazenados no arquivo .sln, embora você possa escrever intencionalmente as informações do projeto para o arquivo .sln, se você optar por fazê-lo. Para obter mais informações sobre persistência, consulte [Project Persistence](../../extensibility/internals/project-persistence.md) and [Opening and Saving Project Its](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Cabeçalho de arquivo

O cabeçalho de um arquivo .sln é assim:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definições

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Cabeçalho padrão que define a versão do formato do arquivo.

`# Visual Studio 15`\
A versão principal do Visual Studio que (mais recentemente) salvou este arquivo de solução. Essas informações controlam o número da versão no ícone da solução.

`VisualStudioVersion = 15.0.26730.15`\
A versão completa do Visual Studio que (mais recentemente) salvou o arquivo de solução. Se o arquivo de solução for salvo por uma versão mais recente do Visual Studio que tem a mesma versão principal, esse valor não será atualizado de modo a diminuir o churn nos arquivos de solução.

`MinimumVisualStudioVersion = 10.0.40219.1`\
A versão mínima (mais antiga) do Visual Studio que pode abrir este arquivo de solução.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definições

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Cabeçalho padrão que define a versão do formato do arquivo.

`# Visual Studio Version 16`\
A versão principal do Visual Studio que (mais recentemente) salvou este arquivo de solução. Essas informações controlam o número da versão no ícone da solução.

`VisualStudioVersion = 16.0.28701.123`\
A versão completa do Visual Studio que (mais recentemente) salvou o arquivo de solução. Se o arquivo de solução for salvo por uma versão mais recente do Visual Studio que tenha a mesma versão principal, esse valor não será atualizado para diminuir a rotatividade no arquivo.

`MinimumVisualStudioVersion = 10.0.40219.1`\
A versão mínima (mais antiga) do Visual Studio que pode abrir este arquivo de solução.

::: moniker-end

## <a name="file-body"></a>Corpo de arquivo

O corpo de um arquivo .sln consiste `GlobalSection`em várias seções rotuladas, como esta:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Para carregar uma solução, o ambiente executa a seguinte seqüência de tarefas:

1. O ambiente lê a seção Global do arquivo .sln e processa todas as seções marcadas `preSolution`. Neste arquivo de exemplo, há uma dessas afirmações:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Quando o ambiente `GlobalSection('name')` lê a tag, ele mapeia o nome para um VSPackage usando o registro. O nome-chave deve existir no registro\\ em [HKLM<ID De registro de aplicativo Raiz\>\SoluçãoPersistence\AggregateGUIDs]. O valor padrão das chaves é o Pacote GUID (REG_SZ) do VSPackage que escreveu as entradas.

2. O ambiente carrega o VSPackage, chama `QueryInterface` o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> VSPackage para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> a interface e chama o método com os dados na seção para que o VSPackage possa armazenar os dados. O ambiente repete esse `preSolution` processo para cada seção.

3. O ambiente itera através dos blocos de persistência do projeto. Neste caso, há um projeto.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Esta declaração contém o guia de projeto exclusivo e o tipo de projeto GUID. Essas informações são usadas pelo ambiente para encontrar o arquivo do projeto ou arquivos pertencentes à solução e o VSPackage necessário para cada projeto. O projeto GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> é passado para carregar o VSPackage específico relacionado ao projeto, em seguida, o projeto é carregado pelo VSPackage. Neste caso, o VSPackage que é carregado para este projeto é Visual Basic.

   Cada projeto pode persistir um ID de instância de projeto único para que ele possa ser acessado conforme necessário por outros projetos na solução. Idealmente, se a solução e os projetos estiverem sob controle de código fonte, o caminho para o projeto deve ser relativo ao caminho para a solução. Quando a solução é carregada pela primeira vez, os arquivos do projeto não podem estar na máquina do usuário. Ao ter o arquivo do projeto armazenado no servidor em relação ao arquivo de solução, é relativamente simples que o arquivo do projeto seja encontrado e copiado para a máquina do usuário. Em seguida, ele copia e carrega o resto dos arquivos necessários para o projeto.

4. Com base nas informações contidas na seção de projeto do arquivo .sln, o ambiente carrega cada arquivo do projeto. O projeto em si é então responsável por preencher a hierarquia do projeto e carregar quaisquer projetos aninhados.

5. Depois que todas as seções do arquivo .sin são processadas, a solução é exibida no Solution Explorer e está pronta para modificações pelo usuário.

Se qualquer VSPackage que implementa um projeto na <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> solução falhar de carregar, o método é chamado e todos os outros projetos da solução terão a chance de ignorar as alterações que ele pode ter feito durante o carregamento. Se ocorrerem erros de análise, o máximo de informações possível será preservada com os arquivos da solução e o ambiente exibe uma caixa de diálogo avisando o usuário de que a solução está corrompida.

Quando a solução é salva <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> ou fechada, o método é chamado e passado para a hierarquia para ver se foram feitas alterações na solução que precisam ser inseridas no arquivo .sln. Um valor nulo, `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>repassado para dentro, indica que as informações estão sendo persistidas para a solução. Se o valor não for nulo, as informações persistindo são <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> para um projeto específico, determinado pelo ponteiro para a interface.

Se houver informações a serem <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> salvas, a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> será chamada com um ponteiro para o método. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> método é então chamado pelo ambiente para recuperar `IPropertyBag` os pares de valor de nome da interface e escrever as informações para o arquivo .sln.

`SaveSolutionProps`e `WriteSolutionProps` os objetos são chamados recursivamente pelo ambiente `IPropertyBag` para recuperar informações a serem salvas da interface até que todas as alterações tenham sido inseridas no arquivo .sln. Desta forma, você pode garantir que as informações serão persistidas com a solução e disponíveis na próxima vez que a solução for aberta.

Cada VSPackage carregado é enumerado para ver se ele tem algo a salvar em arquivo .sln. É apenas no tempo de carga que as chaves do registro são consultadas. O ambiente sabe de todos os pacotes carregados porque eles estão na memória no momento em que a solução é salva.

Apenas o arquivo .sln contém `preSolution` `postSolution` entradas nas seções e. Não há seções semelhantes no arquivo .suo, uma vez que a solução precisa que essas informações sejam carregadas corretamente. O arquivo .suo contém opções específicas do usuário, como notas privadas, que não se destinam a ser compartilhadas ou colocadas sob controle de código fonte.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [Arquivo .Suo (Solution User Options)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Soluções](../../extensibility/internals/solutions-overview.md)
