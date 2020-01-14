---
title: Atualizando projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9170532746dfc61cdec6636fb669676a94535de1
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848776"
---
# <a name="upgrading-projects"></a>Atualizando projetos

As alterações no modelo de projeto de uma versão do Visual Studio para a próxima podem exigir que projetos e soluções sejam atualizados para que possam ser executados na versão mais recente. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] fornece interfaces que podem ser usadas para implementar o suporte de atualização em seus próprios projetos.

## <a name="upgrade-strategies"></a>Estratégias de atualização

Para dar suporte a uma atualização, a implementação do sistema do projeto deve definir e implementar uma estratégia de atualização. Para determinar sua estratégia, você pode optar por dar suporte a backups lado a lado (SxS), copiar backup ou ambos.

- Backup SxS significa que um projeto copia apenas os arquivos que precisam ser atualizados no local, adicionando um sufixo de nome de arquivo adequado, por exemplo, ". old".

- Backup de cópia significa que um projeto copia todos os itens de projeto para um local de backup fornecido pelo usuário. Os arquivos relevantes no local do projeto original são atualizados.

## <a name="how-upgrade-works"></a>Como funciona a atualização

Quando uma solução criada em uma versão anterior do Visual Studio é aberta em uma versão mais recente, o IDE verifica o arquivo da solução para determinar se ele precisa ser atualizado. Se a atualização for necessária, o **Assistente de atualização** será iniciado automaticamente para orientar o usuário durante o processo de atualização.

Quando uma solução precisa ser atualizada, ela consulta cada fábrica de projetos em busca de sua estratégia de atualização. A estratégia determina se a fábrica de projetos dá suporte ao backup de cópia ou de um conjunto. As informações são enviadas para o **Assistente de atualização**, que coleta as informações necessárias para o backup e apresenta as opções aplicáveis ao usuário.

### <a name="multi-project-solutions"></a>Soluções de vários projetos

Se uma solução contiver vários projetos e as estratégias de atualização forem diferentes, como C++ quando um projeto oferece suporte apenas a backup de SxS e um projeto Web que oferece suporte apenas a backup de cópia, as fábricas de projeto devem negociar a estratégia de atualização.

A solução consulta cada fábrica de projetos para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Em seguida, ele chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver se arquivos de projeto globais precisam de atualização e para determinar as estratégias de atualização com suporte. O **Assistente de atualização** é invocado.

Depois que o usuário concluir o assistente, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> será chamado em cada fábrica do projeto para executar a atualização real. Para facilitar o backup, os métodos IVsProjectUpgradeViaFactory fornecem o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> para registrar em log os detalhes do processo de atualização. Este serviço não pode ser armazenado em cache.

Depois de atualizar todos os arquivos globais relevantes, cada fábrica de projetos pode optar por criar uma instância de um projeto. A implementação do projeto deve dar suporte a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> é chamado para atualizar todos os itens de projeto relevantes.

> [!NOTE]
> O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> não fornece o serviço SVsUpgradeLogger. Esse serviço pode ser obtido chamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.

## <a name="best-practices"></a>Práticas recomendadas

Use o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> para verificar se você pode editar um arquivo antes de editá-lo e pode salvá-lo antes de salvá-lo. Isso ajudará as implementações de backup e atualização a manipular arquivos de projeto sob controle do código-fonte, arquivos com permissões insuficientes e assim por diante.

Use o serviço de <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> durante todas as fases de backup e atualização para fornecer informações sobre o êxito ou a falha do processo de atualização.

Para obter mais informações sobre como fazer backup e atualizar projetos, consulte os comentários para IVsProjectUpgrade em vsshell2. idl.

## <a name="upgrading-custom-projects"></a>Atualizando projetos personalizados

Se você alterar as informações mantidas no arquivo de projeto entre versões diferentes do Visual Studio do seu produto, será necessário dar suporte à atualização do arquivo de projeto da versão antiga para a nova. Para dar suporte à atualização que permite que você participe do **Assistente de conversão do Visual Studio**, implemente a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Essa interface contém o único mecanismo disponível para atualização de cópia. A atualização do projeto acontece como parte da solução é aberta. A interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> é implementada pela fábrica do projeto ou deve ser obtida pelo menos na fábrica do projeto.

O mecanismo antigo que usa a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> ainda tem suporte, mas atualiza conceitualmente o sistema de projeto como parte do projeto aberto. A interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, portanto, é chamada pelo ambiente do Visual Studio, mesmo que a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> seja chamada ou implementada. Essa abordagem permite que você use <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> para implementar a cópia e projetar apenas partes da atualização e delegar o restante do trabalho a ser feito no local (possivelmente no novo local) pela interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

Para obter um exemplo de implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, consulte [exemplos de VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Os cenários a seguir surgem com atualizações de projeto:

- Se o arquivo for de um formato mais recente do que o projeto pode dar suporte, ele deverá retornar um erro informando isso. Isso pressupõe que a versão mais antiga do seu produto inclui código para verificar a versão.

- Se o sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> for especificado no método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, a atualização será implementada como uma atualização in-loco antes da abertura do projeto.

- Se o sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> for especificado no método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>, a atualização será implementada como uma atualização de cópia.

- Se o sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> for especificado na chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, o usuário será solicitado pelo ambiente para atualizar o arquivo de projeto como uma atualização in-loco, depois que o projeto for aberto. Por exemplo, o ambiente solicita que o usuário atualize quando o usuário abre uma versão mais antiga da solução.

- Se o sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> não for especificado na chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, você deverá solicitar que o usuário atualize o arquivo de projeto.

     A seguir está um exemplo de mensagem de prompt de atualização:

     "O projeto ' %1 ' foi criado com uma versão mais antiga do Visual Studio. Se você abri-lo com esta versão do Visual Studio, talvez não consiga abri-lo com versões mais antigas do Visual Studio. Deseja continuar e abrir este projeto? "

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar o IVsProjectUpgradeViaFactory

1. Implemente o método da interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, especificamente o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> na implementação da fábrica do projeto, ou torne as implementações que podem ser chamadas da implementação da fábrica do projeto.

2. Se você quiser fazer uma atualização in-loco como parte da abertura da solução, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> como o parâmetro `VSPUVF_FLAGS` em sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

3. Se você quiser fazer uma atualização in-loco como parte da abertura da solução, forneça o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> como o parâmetro `VSPUVF_FLAGS` em sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>.

4. Para as etapas 2 e 3, as etapas de atualização de arquivo reais, usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, podem ser implementadas conforme descrito na seção "Implementando `IVsProjectUpgade`" abaixo, ou você pode delegar a atualização de arquivo real para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

5. Use os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para postar mensagens relacionadas à atualização para o usuário usando o assistente de migração do Visual Studio.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> interface é usada para implementar qualquer tipo de atualização de arquivo que precise ocorrer como parte da atualização do projeto. Essa interface não é chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, mas é fornecida como um mecanismo para atualizar arquivos que fazem parte do sistema de projeto, mas o sistema de projeto principal pode não estar diretamente ciente do. Por exemplo, essa situação pode ocorrer se os arquivos relacionados ao compilador e as propriedades não são tratados pela mesma equipe de desenvolvimento que lida com o restante do sistema do projeto.

### <a name="ivsprojectupgrade-implementation"></a>Implementação de IVsProjectUpgrade

Se o sistema do projeto implementar apenas <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, ele não poderá participar do **Assistente de conversão do Visual Studio**. No entanto, mesmo se você implementar a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ainda poderá delegar a atualização do arquivo para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação.

#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar o IVsProjectUpgrade

1. Quando um usuário tenta abrir um projeto, o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> é chamado pelo ambiente depois que o projeto é aberto e antes que qualquer outra ação do usuário possa ser executada no projeto. Se o usuário já tiver sido solicitado a atualizar a solução, o sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> será passado no parâmetro `grfUpgradeFlags`. Se o usuário abrir um projeto diretamente, como usando o comando **Adicionar projeto existente** , o sinalizador de <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> não será passado e o projeto precisará solicitar que o usuário faça a atualização.

2. Em resposta à chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>, o projeto deve avaliar se o arquivo de projeto é atualizado. Se o projeto não precisar atualizar o tipo de projeto para uma nova versão, ele poderá simplesmente retornar o sinalizador de <xref:Microsoft.VisualStudio.VSConstants.S_OK>.

3. Se o projeto precisar atualizar o tipo de projeto para uma nova versão, ele deverá determinar se o arquivo de projeto pode ser modificado chamando o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passando um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> para o parâmetro `rgfQueryEdit`. O projeto precisa fazer o seguinte:

    - Se o valor de `VSQueryEditResult` retornado no parâmetro `pfEditCanceled` for <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>, a atualização poderá continuar porque o arquivo de projeto pode ser gravado.

    - Se o valor de `VSQueryEditResult` retornado no parâmetro `pfEditCanceled` for <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e o valor de `VSQueryEditResult` tiver o conjunto de bits <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> deverá retornar uma falha, pois os usuários devem resolver o problema de permissões em si. O projeto deve fazer o seguinte:

         Relate o erro ao usuário chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> e retorne o código de erro <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> para <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.

    - Se o valor de `VSQueryEditResult` for <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e o valor de `VSQueryEditResultFlags` tiver o conjunto de bits <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>, será necessário fazer check-out do arquivo de projeto chamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...).

4. Se a chamada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> no arquivo de projeto fizer o check-out do arquivo e a versão mais recente a ser recuperada, o projeto será descarregado e recarregado. O método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> é chamado novamente depois que outra instância do projeto é criada. Nesta segunda chamada, o arquivo de projeto pode ser gravado em disco; é recomendável que o projeto salve uma cópia do arquivo de projeto no formato anterior com um. Extensão antiga, faça as alterações de atualização necessárias e salve o arquivo de projeto no novo formato. Novamente, se qualquer parte do processo de atualização falhar, o método deverá indicar falha retornando <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>. Isso faz com que o projeto seja descarregado em Gerenciador de Soluções.

     É importante entender o processo completo que ocorre no ambiente para o caso em que a chamada para o método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (especificando um valor de ReportOnly) retorna o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> e os sinalizadores de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc>.

5. O usuário tenta abrir o arquivo de projeto.

6. O ambiente chama sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

7. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> retornar `true`, o ambiente chamará sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>.

8. O ambiente chama sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> para abrir o arquivo e inicializar o objeto de projeto, por exemplo, Projeto1.

9. O ambiente chama sua implementação de `IVsProjectUpgrade::UpgradeProject` para determinar se o arquivo de projeto precisa ser atualizado.

10. Você chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passa um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> para o parâmetro `rgfQueryEdit`.

11. O ambiente retorna <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> para `VSQueryEditResult` e o bit de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> é definido em `VSQueryEditResultFlags`.

12. Sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> chama `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting><xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>).

Essa chamada pode fazer com que uma nova cópia do arquivo de projeto seja verificada e a versão mais recente seja recuperada, bem como a necessidade de recarregar o arquivo de projeto. Neste ponto, acontece uma das duas coisas:

- Se você manipular sua própria recarga de projeto, o ambiente chama sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT). Quando você receber essa chamada, recarregue a primeira instância do seu projeto (Projeto1) e Continue atualizando o arquivo de projeto. O ambiente sabe que você lida com sua própria recarga de projeto se retornar `true` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>).

- Se você não tratar sua própria recarga de projeto, você retornará `false` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>). Nesse caso, antes que <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) retorne, o ambiente cria outra nova instância do seu projeto, por exemplo, Projeto2, da seguinte maneira:

    1. O ambiente chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> no seu primeiro objeto de projeto, Projeto1, colocando esse objeto no estado inativo.

    2. O ambiente chama sua implementação de `IVsProjectFactory::CreateProject` para criar uma segunda instância do seu projeto, Projeto2.

    3. O ambiente chama sua implementação de `IPersistFileFormat::Load` para abrir o arquivo e inicializar o segundo objeto de projeto, Projeto2.

    4. O ambiente chama `IVsProjectUpgrade::UpgradeProject` pela segunda vez para determinar se o objeto do projeto deve ser atualizado. No entanto, essa chamada é feita em uma nova instância do projeto, em segundo lugar, no Projeto2. Este é o projeto que é aberto na solução.

        > [!NOTE]
        > Na instância em que seu primeiro projeto, Projeto1, é colocado no estado inativo, você deve retornar <xref:Microsoft.VisualStudio.VSConstants.S_OK> da primeira chamada para sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>.

    5. Você chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> e passa um valor de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> para o parâmetro `rgfQueryEdit`.

    6. O ambiente retorna <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> e a atualização pode continuar porque o arquivo de projeto pode ser gravado.

Se você falhar ao atualizar, retorne <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> de `IVsProjectUpgrade::UpgradeProject`. Se nenhuma atualização for necessária ou se você optar por não atualizar, trate a chamada de `IVsProjectUpgrade::UpgradeProject` como não operacional. Se você retornar <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>, um nó de espaço reservado será adicionado à solução para seu projeto.

## <a name="upgrading-project-items"></a>Atualizando itens do projeto

Se você adicionar ou gerenciar itens dentro de sistemas de projeto que não implementar, talvez seja necessário participar do processo de atualização do projeto. O Crystal Reports é um exemplo de um item que pode ser adicionado ao sistema de projeto.

Normalmente, os implementadores de item de projeto desejam aproveitar um projeto já totalmente instanciado e atualizado, pois eles precisam saber quais são as referências do projeto e quais outras propriedades do projeto existem para tomar uma decisão de atualização.

### <a name="to-get-the-project-upgrade-notification"></a>Para obter a notificação de atualização do projeto

1. Defina o sinalizador <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> (definido em vsshell80. idl) na implementação do item do projeto. Isso faz com que o item de projeto VSPackage o carregamento automático quando o Shell do Visual Studio determina que um sistema de projeto está no processo de atualização.

2. Avise a interface de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> por meio do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>.

3. A interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> é disparada depois que a implementação do sistema do projeto concluiu suas operações de atualização e o novo projeto atualizado é criado. Dependendo do cenário, a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> é acionada após os métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A>.

### <a name="to-upgrade-the-project-item-files"></a>Para atualizar os arquivos de item de projeto

1. Você deve gerenciar cuidadosamente o processo de backup de arquivo em sua implementação de item de projeto. Isso se aplica em particular para um backup lado a lado, em que o parâmetro `fUpgradeFlag` do método <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> é definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>, onde os arquivos cujo backup foi feito são colocados em arquivos no lado que são designados como ". old". Os arquivos de backup mais antigos que a hora do sistema em que o projeto foi atualizado podem ser designados como obsoletos. Além disso, eles podem ser substituídos, a menos que você execute etapas específicas para evitar isso.

2. No momento em que o item do projeto recebe uma notificação da atualização do projeto, o **Assistente de conversão do Visual Studio** ainda é exibido. Portanto, você deve usar os métodos da interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> para fornecer mensagens de atualização para a interface do usuário do assistente.

## <a name="see-also"></a>Veja também

- [Projetos](../../extensibility/internals/projects.md)
