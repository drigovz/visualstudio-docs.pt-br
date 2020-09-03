---
title: Solução (. Sln) arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d9e045ab707620fe985e34174238081f6168e5af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154966"
---
# <a name="solution-sln-file"></a>Arquivo de solução (.Sln)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uma solução é uma estrutura para organizar projetos no Visual Studio. A solução mantém as informações de estado de projetos em arquivos. sln (baseado em texto, compartilhado) e. suo (opções de solução binária, específicas do usuário). Para obter mais informações sobre arquivos. suo, consulte [Opções de usuário da solução (. Suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Se seu VSPackage for carregado como resultado de ser referenciado no arquivo. sln, o ambiente chamará <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> para ler no arquivo. sln.  
  
 O arquivo. sln contém informações baseadas em texto que o ambiente usa para localizar e carregar os parâmetros de valor de nome para os dados persistentes e o projeto VSPackages que faz referência a ele. Quando um usuário abre uma solução, o ambiente percorre as `preSolution` informações, `Project` e `postSolution` no arquivo. sln para carregar a solução, os projetos dentro da solução e todas as informações persistentes anexadas à solução.  
  
 Cada arquivo do projeto contém informações adicionais lidas pelo ambiente para popular a hierarquia com os itens desse projeto. A persistência de dados de hierarquia é controlada pelo projeto; os dados normalmente não são armazenados no arquivo. sln, embora seja possível gravar intencionalmente as informações do projeto no arquivo. sln se você optar por fazer isso. Para obter mais informações relacionadas à persistência, consulte [persistência do projeto](../../extensibility/internals/project-persistence.md) e [abertura e salvamento de itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Conteúdo do arquivo de solução  
 O arquivo. sln consiste em várias seções, conforme ilustrado no código a seguir.  
  
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
  
 Para carregar uma solução, o ambiente executa a seguinte sequência de tarefas.  
  
1. O ambiente lê a seção global do arquivo. sln e processa todas as seções marcadas `preSolution` . Nesse caso, há uma dessas instruções:  
  
   ```  
   GlobalSection(SolutionConfiguration) = preSolution  
        ConfigName.0 = Debug  
        ConfigName.1 = Release  
   ```  
  
    Quando o ambiente lê a `GlobalSection('name')` marca, ele mapeia o nome para um VSPackage usando o registro. O nome da chave deve existir no registro em [HKLM \\<ID do aplicativo \SolutionPersistence\AggregateGUIDs raiz do registro \> ]. O valor padrão das chaves é o GUID do pacote (REG_SZ) do VSPackage que gravou as entradas.  
  
2. O ambiente carrega o VSPackage, chama o `QueryInterface` VSPackage para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface e chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> método com os dados na seção para que o VSPackage possa armazenar os dados. O ambiente repete esse processo para cada `preSolution` seção.  
  
3. O ambiente percorre os blocos de persistência do projeto. Nesse caso, há um projeto.  
  
   ```  
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
   EndProject  
   ```  
  
    Essa instrução contém o GUID do projeto exclusivo e o GUID do tipo de projeto. Essas informações são usadas pelo ambiente para localizar o arquivo de projeto ou arquivos pertencentes à solução e o VSPackage necessário para cada projeto. O GUID do projeto é passado para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> para carregar o VSPackage específico relacionado ao projeto e, em seguida, o projeto é carregado pelo VSPackage. Nesse caso, o VSPackage que é carregado para esse projeto é Visual Basic.  
  
    Cada projeto pode persistir uma ID de instância de projeto exclusiva para que possa ser acessado conforme necessário por outros projetos na solução. Idealmente, se a solução e os projetos estiverem sob controle do código-fonte, o caminho para o projeto deve ser relativo ao caminho para a solução. Quando a solução é carregada pela primeira vez, os arquivos de projeto não podem estar na máquina do usuário. Com o arquivo de projeto armazenado no servidor em relação ao arquivo de solução, é relativamente simples que o arquivo de projeto seja encontrado e copiado para o computador do usuário. Em seguida, ele copia e carrega o restante dos arquivos necessários para o projeto.  
  
4. Com base nas informações contidas na seção projeto do arquivo. sln, o ambiente carrega cada arquivo de projeto. O projeto em si é, então, responsável por preencher a hierarquia do projeto e carregar quaisquer projetos aninhados.  
  
5. Depois que todas as seções do arquivo. sln são processadas, a solução é exibida no Gerenciador de Soluções e está pronta para modificação pelo usuário.  
  
   Se qualquer VSPackage que implemente um projeto na solução falhar ao ser carregado, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> método será chamado e todos os outros projetos na solução terão a oportunidade de ignorar as alterações que podem ter sido feitas durante o carregamento. Se ocorrerem erros de análise, o máximo de informações possível é preservado com os arquivos da solução e o ambiente exibe uma caixa de diálogo avisando o usuário de que a solução está corrompida.  
  
   Quando a solução é salva ou fechada, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> método é chamado e passado para a hierarquia para ver se foram feitas alterações na solução que precisam ser inseridas no arquivo. sln. Um valor nulo, passado para `QuerySaveSolutionProps` no <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , indica que as informações estão sendo persistidas para a solução. Se o valor não for nulo, as informações persistentes serão para um projeto específico, determinado pelo ponteiro para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface.  
  
   Se houver informações a serem salvas, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interface será chamada com um ponteiro para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> método. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> método é então chamado pelo ambiente para recuperar os pares de nome-valor da `IPropertyBag` interface e gravar as informações no arquivo. sln.  
  
   `SaveSolutionProps` e os `WriteSolutionProps` objetos são chamados recursivamente pelo ambiente para recuperar informações a serem salvas da `IPropertyBag` interface até que todas as alterações tenham sido inseridas no arquivo. sln. Dessa forma, você pode garantir que as informações serão persistidas com a solução e disponíveis na próxima vez em que a solução for aberta.  
  
   Cada VSPackage carregada é enumerada para ver se há algo a ser salvo no arquivo. sln. É apenas no momento da carga que as chaves do registro são consultadas. O ambiente conhece todos os pacotes carregados porque eles estão na memória no momento em que a solução é salva.  
  
   Somente o arquivo. sln contém entradas nas `preSolution` seções e `postSolution` . Não há seções semelhantes no arquivo. suo, pois a solução precisa que essas informações sejam carregadas corretamente. O arquivo. suo contém opções específicas do usuário, como notas particulares, que não devem ser compartilhadas ou colocadas sob controle do código-fonte.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opções de usuário da solução (. Suo) arquivo](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluções](../../extensibility/internals/solutions-overview.md)
