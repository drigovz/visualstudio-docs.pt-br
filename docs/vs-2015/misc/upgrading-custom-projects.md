---
title: Atualização de Projetos Personalizados | Microsoft Docs
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
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037201"
---
# <a name="upgrading-custom-projects"></a>Atualizando projetos personalizados
Se você alterar as informações persistindo no arquivo do projeto entre diferentes versões do Visual Studio do seu produto, então você precisa suportar a atualização do arquivo do projeto da versão antiga para a nova. Para suportar a atualização que permite que você participe <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> do Visual Studio Conversion **Wizard,** implemente a interface. Esta interface contém o único mecanismo disponível para atualização de cópia. A atualização do projeto acontece como parte da solução é aberta. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface é implementada pela fábrica do projeto, ou deve pelo menos ser obtida na fábrica do projeto.  
  
 O antigo mecanismo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> que usa a interface ainda é suportado, mas conceitualmente atualiza o sistema de projeto como parte do projeto aberto. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface é, portanto, chamada pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente mesmo que a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface seja chamada ou implementada. Essa abordagem permite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> que você use para implementar a cópia e projetar apenas partes da atualização, e delegar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> resto do trabalho a ser feito no local (possivelmente no novo local) pela interface.  
  
 Para obter uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>implementação amostral de , consulte [AMOSTRAS VSSDK](../misc/vssdk-samples.md).  
  
 Os seguintes cenários surgem com upgrades de projetos:  
  
- Se o arquivo é de um formato mais novo do que o projeto pode suportar, então ele deve retornar um erro indicando isso. Isso pressupõe que a versão mais antiga do seu produto — por exemplo, Visual Studio .NET 2003 — inclua código para verificar a versão.  
  
- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> a bandeira for <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> especificada no método, a atualização será implementada como uma atualização no local antes da abertura do projeto.  
  
- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> o sinalizador for <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> especificado no método, a atualização será implementada como uma atualização de cópia.  
  
- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> o sinalizador for <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> especificado na chamada, o usuário será solicitado pelo ambiente a atualizar o arquivo do projeto como uma atualização no local, após a abertura do projeto. Por exemplo, o ambiente solicita ao usuário a atualização quando o usuário abre uma versão mais antiga da solução.  
  
- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> o sinalizador não estiver <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> especificado na chamada, então você deve solicitar ao usuário que atualize o arquivo do projeto.  
  
     A seguir está uma mensagem de alerta de upgrade de exemplo:  
  
     "O projeto '%1' foi criado com uma versão mais antiga do Visual Studio. Se você abri-lo com esta versão do Visual Studio, você pode não ser capaz de abri-lo com versões mais antigas do Visual Studio. Você quer continuar e abrir esse projeto?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar iVsProjectUpgradeViaFactory  
  
1. Implemente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> método da interface, especificamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método na implementação da fábrica do projeto, ou torne as implementações callable a partir da implementação da fábrica do projeto.  
  
2. Se você quiser fazer uma atualização no local como parte da <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> abertura `VSPUVF_FLAGS` da solução, forneça a bandeira como parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
3. Se você quiser fazer uma atualização no local como parte da <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> abertura `VSPUVF_FLAGS` da solução, forneça a bandeira como parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.  
  
4. Para ambas as etapas 2 e 3, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>as etapas reais de atualização `IVsProjectUpgade`de arquivo, usando , podem ser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>implementadas conforme descrito na seção "Implementando" abaixo, ou você pode delegar a atualização real do arquivo para .  
  
5. Use os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> postar mensagens relacionadas à atualização para o usuário usando o Visual Studio Migration Wizard.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>interface é usado para implementar qualquer tipo de upgrade de arquivo que precisa acontecer como parte da atualização do projeto. Esta interface não <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>é chamada de , mas é fornecida como um mecanismo para atualizar arquivos que fazem parte do sistema do projeto, mas o sistema principal do projeto pode não estar diretamente ciente. Por exemplo, essa situação pode surgir se os arquivos e propriedades relacionados ao compilador não forem tratados pela mesma equipe de desenvolvimento que lida com o resto do sistema de projeto.  
  
## <a name="ivsprojectupgrade-implementation"></a>Implementação de upgrade do IVsProjectUpgrade  
 Se o seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> sistema de projeto for implementado apenas, ele não poderá participar do **Visual Studio Conversion Wizard**. No entanto, mesmo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> se você implementar a interface, você ainda pode delegar a atualização do arquivo para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar iVsProjectUpgrade  
  
1. Quando um usuário tenta abrir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> um projeto, o método é chamado pelo ambiente após a abertura do projeto e antes que qualquer outra ação do usuário possa ser tomada no projeto. Se o usuário já tinha sido solicitado a <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> atualizar a `grfUpgradeFlags` solução, então o sinalizador é passado no parâmetro. Se o usuário abrir um projeto diretamente, como usando o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> comando Adicionar projeto **existente,** então o sinalizador não será passado e o projeto precisa solicitar que o usuário atualize.  
  
2. Em resposta <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> à chamada, o projeto deve avaliar se o arquivo do projeto foi atualizado. Se o projeto não precisar atualizar o tipo de projeto para <xref:Microsoft.VisualStudio.VSConstants.S_OK> uma nova versão, ele pode simplesmente devolver o sinalizador.  
  
3. Se o projeto precisar atualizar o tipo de projeto para uma nova versão, então <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ele deve determinar <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> se `rgfQueryEdit` o arquivo do projeto pode ser modificado chamando o método e passando um valor de para o parâmetro. O projeto então precisa fazer o seguinte:  
  
   - Se `VSQueryEditResult` o valor retornado `pfEditCanceled` no <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>parâmetro for, então a atualização pode prosseguir porque o arquivo do projeto pode ser gravado.  
  
   - Se `VSQueryEditResult` o valor devolvido `pfEditCanceled` no <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> parâmetro `VSQueryEditResult` for e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> o valor <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> tiver o bit definido, então deve retornar falha, porque os usuários devem resolver as permissões em questão. O projeto deve então fazer o seguinte:  
  
        Reporte o erro ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>usuário ligando . e retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>código de erro para .  
  
   - Se `VSQueryEditResult` o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> valor `VSQueryEditResultFlags` for e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> o valor tiver o bit definido, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>então <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>o arquivo do projeto deve ser verificado por chamada (, ,...).  
  
4. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a chamada no arquivo do projeto fizer com que o arquivo seja verificado e a versão mais recente seja recuperada, o projeto será descarregado e recarregado. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado novamente uma vez que outra instância do projeto é criada. Nesta segunda chamada, o arquivo do projeto pode ser gravado em disco; recomenda-se que o projeto salve uma cópia do arquivo do projeto no formato anterior com um . Extensão OLD, faça as alterações de upgrade necessárias e salve o arquivo do projeto no novo formato. Novamente, se qualquer parte do processo de atualização falhar, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>o método deve indicar falha ao retornar . Isso faz com que o projeto seja descarregado no Solution Explorer.  
  
    É importante entender o processo completo que ocorre no ambiente para <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> o caso em que a chamada <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> para <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> o método (especificando um valor de ReportOnly) retorna e as bandeiras.  
  
5. O usuário tenta abrir o arquivo do projeto.  
  
6. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> chama sua implementação.  
  
7. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`retornar, então o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> ambiente chama sua implementação.  
  
8. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> chama sua implementação para abrir o arquivo e inicializar o objeto do projeto, por exemplo, Project1.  
  
9. O ambiente `IVsProjectUpgrade::UpgradeProject` chama sua implementação para determinar se o arquivo do projeto precisa ser atualizado.  
  
10. Você <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> liga e passa <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> um `rgfQueryEdit` valor para o parâmetro.  
  
11. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> `VSQueryEditResult` retorna <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> para e `VSQueryEditResultFlags`a broca é definida em .  
  
12. Suas <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> chamadas `IVsQueryEditQuerySave::QueryEditFiles` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>implementação ( , ).  
  
    Esta chamada pode fazer com que uma nova cópia do arquivo do projeto seja verificada e a versão mais recente recuperada, bem como a necessidade de recarregar seu arquivo de projeto. Neste ponto, uma das duas coisas acontecem:  
  
- Se você lidar com a recarga do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> seu próprio projeto, então o ambiente chama sua implementação (VSITEMID_ROOT). Quando receber essa chamada, recarregue a primeira instância do seu projeto (Project1) e continue atualizando seu arquivo de projeto. O ambiente sabe que você lida com `true` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>recarga do seu próprio projeto se você voltar para ( ).  
  
- Se você não lidar com a recarga `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> do<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>seu próprio projeto, então você retorna para ( ). Neste caso, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>antes ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags),) retorna, o ambiente cria outra nova instância do seu projeto, por exemplo, O Projeto2, como segue:  
  
  1. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> solicita seu primeiro objeto de projeto, O Projeto1, colocando assim esse objeto no estado inativo.  
  
  2. O ambiente `IVsProjectFactory::CreateProject` chama sua implementação para criar uma segunda instância do seu projeto, o Project2.  
  
  3. O ambiente `IPersistFileFormat::Load` chama sua implementação para abrir o arquivo e inicializar o segundo objeto do projeto, Project2.  
  
  4. O ambiente `IVsProjectUpgrade::UpgradeProject` exige uma segunda vez para determinar se o objeto do projeto deve ser atualizado. No entanto, essa chamada é feita em uma nova, segunda instância do projeto, O Projeto2. Este é o projeto que é aberto na solução.  
  
      > [!NOTE]
      > No caso de seu primeiro projeto, Project1, ser colocado no <xref:Microsoft.VisualStudio.VSConstants.S_OK> estado inativo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> então você deve retornar da primeira chamada para sua implementação. Consulte [Projeto Básico](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) para `IVsProjectUpgrade::UpgradeProject`uma implementação de .  
  
  5. Você <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> liga e passa <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> um `rgfQueryEdit` valor para o parâmetro.  
  
  6. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> retorna e a atualização pode prosseguir porque o arquivo do projeto pode ser escrito.  
  
  Se você não conseguir <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> `IVsProjectUpgrade::UpgradeProject`atualizar, retorne de . Se nenhum upgrade for necessário ou você `IVsProjectUpgrade::UpgradeProject` optar por não atualizar, trate a chamada como uma opção. Se você <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>retornar, um nó de espaço reservado é adicionado à solução para o seu projeto.  
  
## <a name="see-also"></a>Consulte Também  
 [Assistente de conversão do estúdio visual](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [Atualização de itens do projeto](../misc/upgrading-project-items.md)   
 [Projetos](../extensibility/internals/projects.md)