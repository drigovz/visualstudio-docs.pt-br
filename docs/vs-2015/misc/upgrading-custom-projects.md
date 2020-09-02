---
title: Atualizando projetos personalizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: c91013e7d5650e82fd9e5f6e39e28c4609e4fbfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037201"
---
# <a name="upgrading-custom-projects"></a>Atualizando projetos personalizados
Se você alterar as informações mantidas no arquivo de projeto entre versões diferentes do Visual Studio do seu produto, será necessário dar suporte à atualização do arquivo de projeto da versão antiga para a nova. Para dar suporte à atualização que permite que você participe do **Assistente de conversão do Visual Studio**, implemente a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface. Essa interface contém o único mecanismo disponível para atualização de cópia. A atualização do projeto acontece como parte da solução é aberta. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface é implementada pela fábrica do projeto ou deve ser obtida pelo menos no Factory do projeto.  
  
 O mecanismo antigo que usa a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface ainda tem suporte, mas atualiza conceitualmente o sistema de projeto como parte do projeto aberto. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface é, portanto, chamada pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente, mesmo se a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface for chamada ou implementada. Essa abordagem permite que você use <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar a cópia e projetar apenas partes da atualização e delegar o restante do trabalho a ser feito in-loco (possivelmente no novo local) pela <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface.  
  
 Para obter um exemplo de implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , consulte [exemplos de VSSDK](../misc/vssdk-samples.md).  
  
 Os cenários a seguir surgem com atualizações de projeto:  
  
- Se o arquivo for de um formato mais recente do que o projeto pode dar suporte, ele deverá retornar um erro informando isso. Isso pressupõe que a versão mais antiga do seu produto, por exemplo, o Visual Studio .NET 2003, inclui código para verificar a versão.  
  
- Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> sinalizador for especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, a atualização será implementada como uma atualização in-loco, antes da abertura do projeto.  
  
- Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> sinalizador for especificado no <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método, a atualização será implementada como uma atualização de cópia.  
  
- Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador for especificado na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamada, o usuário será solicitado pelo ambiente para atualizar o arquivo de projeto como uma atualização in-loco, depois que o projeto for aberto. Por exemplo, o ambiente solicita que o usuário atualize quando o usuário abre uma versão mais antiga da solução.  
  
- Se o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador não for especificado na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamada, você deverá solicitar que o usuário atualize o arquivo de projeto.  
  
     A seguir está um exemplo de mensagem de prompt de atualização:  
  
     "O projeto ' %1 ' foi criado com uma versão mais antiga do Visual Studio. Se você abri-lo com esta versão do Visual Studio, talvez não consiga abri-lo com versões mais antigas do Visual Studio. Deseja continuar e abrir este projeto? "  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar o IVsProjectUpgradeViaFactory  
  
1. Implemente o método da <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, especificamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método em sua implementação de fábrica do projeto, ou faça as implementações que podem ser chamadas da implementação da fábrica do projeto.  
  
2. Se você quiser fazer uma atualização in-loco como parte da abertura da solução, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como o `VSPUVF_FLAGS` parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
3. Se você quiser fazer uma atualização in-loco como parte da abertura da solução, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> como o `VSPUVF_FLAGS` parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
4. Para as etapas 2 e 3, as etapas de atualização de arquivo reais, usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> , podem ser implementadas conforme descrito na seção "Implementando `IVsProjectUpgade` " abaixo, ou você pode delegar a atualização de arquivo real para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
5. Use os métodos do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para postar mensagens relacionadas à atualização para o usuário usando o assistente de migração do Visual Studio.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> a interface é usada para implementar qualquer tipo de atualização de arquivo que precise ocorrer como parte da atualização do projeto. Essa interface não é chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> , mas é fornecida como um mecanismo para atualizar arquivos que fazem parte do sistema de projeto, mas o sistema de projeto principal talvez não esteja ciente diretamente. Por exemplo, essa situação pode ocorrer se os arquivos relacionados ao compilador e as propriedades não são tratados pela mesma equipe de desenvolvimento que lida com o restante do sistema do projeto.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementação de IVsProjectUpgrade  
 Se o sistema do projeto implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> apenas, ele não poderá participar do **Assistente de conversão do Visual Studio**. No entanto, mesmo se você implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface, ainda poderá delegar a atualização do arquivo para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar o IVsProjectUpgrade  
  
1. Quando um usuário tenta abrir um projeto, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado pelo ambiente depois que o projeto é aberto e antes que qualquer outra ação do usuário possa ser executada no projeto. Se o usuário já tiver sido solicitado a atualizar a solução, o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador será passado no `grfUpgradeFlags` parâmetro. Se o usuário abrir um projeto diretamente, como usando o comando **Adicionar projeto existente** , o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> sinalizador não será passado e o projeto precisará solicitar que o usuário faça a atualização.  
  
2. Em resposta à <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> chamada, o projeto deve avaliar se o arquivo de projeto é atualizado. Se o projeto não precisar atualizar o tipo de projeto para uma nova versão, ele poderá simplesmente retornar o <xref:Microsoft.VisualStudio.VSConstants.S_OK> sinalizador.  
  
3. Se o projeto precisar atualizar o tipo de projeto para uma nova versão, ele deverá determinar se o arquivo de projeto pode ser modificado chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método e passando um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro. O projeto precisa fazer o seguinte:  
  
   - Se o `VSQueryEditResult` valor retornado no `pfEditCanceled` parâmetro for <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> , a atualização poderá continuar porque o arquivo de projeto pode ser gravado.  
  
   - Se o `VSQueryEditResult` valor retornado no `pfEditCanceled` parâmetro for <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e o `VSQueryEditResult` valor tiver o conjunto de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bits, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deverá retornar falha, pois os usuários devem resolver o problema de permissões por conta própria. O projeto deve fazer o seguinte:  
  
        Relate o erro ao usuário chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> . e retorne o <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> código de erro para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> .  
  
   - Se o `VSQueryEditResult` valor for <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e o `VSQueryEditResultFlags` valor tiver o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> conjunto de bits, deverá ser feito o check-out do arquivo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ,...).  
  
4. Se a <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> chamada no arquivo de projeto fizer o check-out do arquivo e a versão mais recente a ser recuperada, o projeto será descarregado e recarregado. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado novamente depois que outra instância do projeto é criada. Nesta segunda chamada, o arquivo de projeto pode ser gravado em disco; é recomendável que o projeto salve uma cópia do arquivo de projeto no formato anterior com um. Extensão antiga, faça as alterações de atualização necessárias e salve o arquivo de projeto no novo formato. Novamente, se qualquer parte do processo de atualização falhar, o método deverá indicar falha retornando <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> . Isso faz com que o projeto seja descarregado em Gerenciador de Soluções.  
  
    É importante entender o processo completo que ocorre no ambiente para o caso em que a chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> método (especificando um valor de ReportOnly) retorna os <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> sinalizadores e.  
  
5. O usuário tenta abrir o arquivo de projeto.  
  
6. O ambiente chama sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementação.  
  
7. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retornar `true` , o ambiente chamará sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementação.  
  
8. O ambiente chama sua <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementação para abrir o arquivo e inicializar o objeto Project, por exemplo, Projeto1.  
  
9. O ambiente chama sua `IVsProjectUpgrade::UpgradeProject` implementação para determinar se o arquivo de projeto precisa ser atualizado.  
  
10. Você chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passa um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro.  
  
11. O ambiente retorna <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para `VSQueryEditResult` e o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bit é definido em `VSQueryEditResultFlags` .  
  
12. Sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação chama `IVsQueryEditQuerySave::QueryEditFiles` ( <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> , <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> ).  
  
    Essa chamada pode fazer com que uma nova cópia do arquivo de projeto seja verificada e a versão mais recente seja recuperada, bem como a necessidade de recarregar o arquivo de projeto. Neste ponto, acontece uma das duas coisas:  
  
- Se você manipular sua própria recarga de projeto, o ambiente chama sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementação (VSITEMID_ROOT). Quando você receber essa chamada, recarregue a primeira instância do seu projeto (Projeto1) e Continue atualizando o arquivo de projeto. O ambiente sabe que você lida com sua própria recarga de projeto se retornar `true` for <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ).  
  
- Se você não tratar sua própria recarga de projeto, você retorna `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ( <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> ). Nesse caso, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags)) retornar, o ambiente cria outra nova instância do projeto, por exemplo, Projeto2, da seguinte maneira:  
  
  1. O ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> seu primeiro objeto de projeto, Projeto1, colocando esse objeto no estado inativo.  
  
  2. O ambiente chama sua `IVsProjectFactory::CreateProject` implementação para criar uma segunda instância do seu projeto, Projeto2.  
  
  3. O ambiente chama sua `IPersistFileFormat::Load` implementação para abrir o arquivo e inicializar o segundo objeto do projeto, Projeto2.  
  
  4. O ambiente chama `IVsProjectUpgrade::UpgradeProject` uma segunda vez para determinar se o objeto do projeto deve ser atualizado. No entanto, essa chamada é feita em uma nova instância do projeto, em segundo lugar, no Projeto2. Este é o projeto que é aberto na solução.  
  
      > [!NOTE]
      > Na instância que seu primeiro projeto, Projeto1, é colocado no estado inativo, você deve retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> da primeira chamada para sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementação. Consulte [projeto básico](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) para uma implementação do `IVsProjectUpgrade::UpgradeProject` .  
  
  5. Você chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passa um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o `rgfQueryEdit` parâmetro.  
  
  6. O ambiente retorna <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> e a atualização pode continuar porque o arquivo de projeto pode ser gravado.  
  
  Se você falhar ao atualizar, retorne <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> do `IVsProjectUpgrade::UpgradeProject` . Se nenhuma atualização for necessária ou se você optar por não atualizar, trate a `IVsProjectUpgrade::UpgradeProject` chamada como não operacional. Se você retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> , um nó de espaço reservado será adicionado à solução para seu projeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Assistente de conversão do Visual Studio](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Atualizando itens do projeto](../misc/upgrading-project-items.md)   
 [Projetos](../extensibility/internals/projects.md)