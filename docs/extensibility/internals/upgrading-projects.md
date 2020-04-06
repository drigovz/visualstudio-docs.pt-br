---
title: Projetos de Atualização | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a99207fc14cf9f462bc1abc88d6fed166ea6523f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704261"
---
# <a name="upgrading-projects"></a>Atualizando projetos

Mudanças no modelo de projeto de uma versão do Visual Studio para a próxima podem exigir que projetos e soluções sejam atualizados para que possam ser executados na versão mais recente. As [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces fornecem interfaces que podem ser usadas para implementar suporte a upgrade em seus próprios projetos.

## <a name="upgrade-strategies"></a>Estratégias de atualização

Para suportar um upgrade, a implementação do sistema de projeto deve definir e implementar uma estratégia de upgrade. Ao determinar sua estratégia, você pode optar por fazer backup lado a lado (SxS), copiar backup ou ambos.

- O backup do SxS significa que um projeto copia apenas os arquivos que precisam ser atualizados no local, adicionando um sufixo de nome de arquivo adequado, por exemplo, ".old".

- Copiar backup significa que um projeto copia todos os itens do projeto para um local de backup fornecido pelo usuário. Os arquivos relevantes no local original do projeto são então atualizados.

## <a name="how-upgrade-works"></a>Como funciona o upgrade

Quando uma solução criada em uma versão anterior do Visual Studio é aberta em uma versão mais recente, o IDE verifica o arquivo de solução para determinar se ele precisa ser atualizado. Se a atualização for necessária, o **Assistente de atualização** é automaticamente lançado para acompanhar o usuário durante o processo de atualização.

Quando uma solução precisa ser atualizada, ela consulta cada fábrica de projetos para sua estratégia de atualização. A estratégia determina se a fábrica do projeto suporta backup de cópia ou backup SxS. As informações são enviadas ao **Assistente de Atualização**, que coleta as informações necessárias para o backup e apresenta as opções aplicáveis ao usuário.

### <a name="multi-project-solutions"></a>Soluções multiprojetos

Se uma solução contém vários projetos e as estratégias de upgrade diferem, como quando um projeto C++ que só suporta backup SxS e um projeto Web que só suporta backup de cópia, as fábricas de projetos devem negociar a estratégia de upgrade.

A solução consulta cada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>fábrica de projetos para . Em seguida, ele liga <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> para ver se os arquivos globais do projeto precisam ser atualizados e determinar as estratégias de upgrade suportadas. O **Assistente de Atualização** é então invocado.

Depois que o usuário <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> completa o assistente, é chamado em cada fábrica de projeto para executar a atualização real. Para facilitar o backup, os métodos <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> IVsProjectUpgradeViaFactory fornecem o serviço para registrar os detalhes do processo de atualização. Este serviço não pode ser armazenado em cache.

Depois de atualizar todos os arquivos globais relevantes, cada fábrica de projetos pode optar por instanciar um projeto. A implementação <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>do projeto deve apoiar . O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é então chamado para atualizar todos os itens de projeto relevantes.

> [!NOTE]
> O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método não fornece o serviço SVsUpgradeLogger. Este serviço pode ser <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>obtido ligando.

## <a name="best-practices"></a>Práticas Recomendadas

Use <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> o serviço para verificar se você pode editar um arquivo antes de editá-lo e pode salvá-lo antes de salvá-lo. Isso ajudará suas implementações de backup e upgrade a lidar com arquivos de projeto sob controle de origem, arquivos com permissões insuficientes e assim por diante.

Use <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> o serviço durante todas as fases de backup e atualização para fornecer informações sobre o sucesso ou falha do processo de atualização.

Para obter mais informações sobre backup e atualização de projetos, consulte os comentários de IVsProjectUpgrade em vsshell2.idl.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>Atualizando projetos personalizados

Se você alterar as informações persistindo no arquivo do projeto entre diferentes versões do Visual Studio do seu produto, então você precisa suportar a atualização do arquivo do projeto da versão antiga para a nova. Para suportar a atualização que permite que você participe <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> do Visual Studio Conversion **Wizard,** implemente a interface. Esta interface contém o único mecanismo disponível para atualização de cópia. A atualização do projeto acontece como parte da solução é aberta. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interface é implementada pela fábrica do projeto, ou deve pelo menos ser obtida na fábrica do projeto.

O antigo mecanismo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> que usa a interface ainda é suportado, mas conceitualmente atualiza o sistema de projeto como parte do projeto aberto. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interface é, portanto, chamada pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> ambiente Visual Studio, mesmo que a interface seja chamada ou implementada. Essa abordagem permite <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> que você use para implementar a cópia e projetar apenas partes da atualização, e delegar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> resto do trabalho a ser feito no local (possivelmente no novo local) pela interface.

Para obter uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>implementação amostral de , consulte [AMOSTRAS VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

Os seguintes cenários surgem com upgrades de projetos:

- Se o arquivo é de um formato mais novo do que o projeto pode suportar, então ele deve retornar um erro indicando isso. Isso pressupõe que a versão mais antiga do seu produto inclui código para verificar a versão.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> a bandeira for <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> especificada no método, a atualização será implementada como uma atualização no local antes da abertura do projeto.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> o sinalizador for <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> especificado no método, a atualização será implementada como uma atualização de cópia.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> o sinalizador for <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> especificado na chamada, o usuário será solicitado pelo ambiente a atualizar o arquivo do projeto como uma atualização no local, após a abertura do projeto. Por exemplo, o ambiente solicita ao usuário a atualização quando o usuário abre uma versão mais antiga da solução.

- Se <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> o sinalizador não estiver <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> especificado na chamada, então você deve solicitar ao usuário que atualize o arquivo do projeto.

     A seguir está uma mensagem de alerta de upgrade de exemplo:

     "O projeto '%1' foi criado com uma versão mais antiga do Visual Studio. Se você abri-lo com esta versão do Visual Studio, você pode não ser capaz de abri-lo com versões mais antigas do Visual Studio. Você quer continuar e abrir esse projeto?"

### <a name="to-implement-ivsprojectupgradeviafactory"></a>Para implementar iVsProjectUpgradeViaFactory

1. Implemente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> método da interface, especificamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método na implementação da fábrica do projeto, ou torne as implementações callable a partir da implementação da fábrica do projeto.

2. Se você quiser fazer uma atualização no local como parte da <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> abertura `VSPUVF_FLAGS` da solução, forneça a bandeira como parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.

3. Se você quiser fazer uma atualização no local como parte da <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> abertura `VSPUVF_FLAGS` da solução, forneça a bandeira como parâmetro em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementação.

4. Para ambas as etapas 2 e 3, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>as etapas reais de atualização `IVsProjectUpgade`de arquivo, usando , podem ser <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>implementadas conforme descrito na seção "Implementando" abaixo, ou você pode delegar a atualização real do arquivo para .

5. Use os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> postar mensagens relacionadas à atualização para o usuário usando o Visual Studio Migration Wizard.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade>interface é usado para implementar qualquer tipo de upgrade de arquivo que precisa acontecer como parte da atualização do projeto. Esta interface não <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>é chamada de , mas é fornecida como um mecanismo para atualizar arquivos que fazem parte do sistema do projeto, mas o sistema principal do projeto pode não estar diretamente ciente. Por exemplo, essa situação pode surgir se os arquivos e propriedades relacionados ao compilador não forem tratados pela mesma equipe de desenvolvimento que lida com o resto do sistema de projeto.

### <a name="ivsprojectupgrade-implementation"></a>Implementação de upgrade do IVsProjectUpgrade

Se o seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> sistema de projeto for implementado apenas, ele não poderá participar do **Visual Studio Conversion Wizard**. No entanto, mesmo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> se você implementar a interface, você ainda pode delegar a atualização do arquivo para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementação.

#### <a name="to-implement-ivsprojectupgrade"></a>Para implementar iVsProjectUpgrade

1. Quando um usuário tenta abrir <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> um projeto, o método é chamado pelo ambiente após a abertura do projeto e antes que qualquer outra ação do usuário possa ser tomada no projeto. Se o usuário já tinha sido solicitado a <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> atualizar a `grfUpgradeFlags` solução, então o sinalizador é passado no parâmetro. Se o usuário abrir um projeto diretamente, como usando o <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> comando Adicionar projeto **existente,** então o sinalizador não será passado e o projeto precisa solicitar que o usuário atualize.

2. Em resposta <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> à chamada, o projeto deve avaliar se o arquivo do projeto foi atualizado. Se o projeto não precisar atualizar o tipo de projeto para <xref:Microsoft.VisualStudio.VSConstants.S_OK> uma nova versão, ele pode simplesmente devolver o sinalizador.

3. Se o projeto precisar atualizar o tipo de projeto para uma nova versão, então <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ele deve determinar <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> se `rgfQueryEdit` o arquivo do projeto pode ser modificado chamando o método e passando um valor de para o parâmetro. O projeto então precisa fazer o seguinte:

    - Se `VSQueryEditResult` o valor retornado `pfEditCanceled` no <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>parâmetro for, então a atualização pode prosseguir porque o arquivo do projeto pode ser gravado.

    - Se `VSQueryEditResult` o valor devolvido `pfEditCanceled` no <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> parâmetro `VSQueryEditResult` for e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> o valor <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> tiver o bit definido, então deve retornar falha, porque os usuários devem resolver as permissões em questão. O projeto deve então fazer o seguinte:

         Denuncie o erro ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> usuário <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> ligando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>e retorne o código de erro para .

    - Se `VSQueryEditResult` o <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> valor `VSQueryEditResultFlags` for e <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> o valor tiver o bit definido, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>então <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>o arquivo do projeto deve ser verificado por chamada (, ,...).

4. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> a chamada no arquivo do projeto fizer com que o arquivo seja verificado e a versão mais recente seja recuperada, o projeto será descarregado e recarregado. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> método é chamado novamente uma vez que outra instância do projeto é criada. Nesta segunda chamada, o arquivo do projeto pode ser gravado em disco; recomenda-se que o projeto salve uma cópia do arquivo do projeto no formato anterior com um . Extensão OLD, faça as alterações de upgrade necessárias e salve o arquivo do projeto no novo formato. Novamente, se qualquer parte do processo de atualização falhar, <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>o método deve indicar falha ao retornar . Isso faz com que o projeto seja descarregado no Solution Explorer.

     É importante entender o processo completo que ocorre no ambiente para <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> o caso em que a chamada <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> para <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> o método (especificando um valor de ReportOnly) retorna e as bandeiras.

5. O usuário tenta abrir o arquivo do projeto.

6. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> chama sua implementação.

7. Se <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> `true`retornar, então o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> ambiente chama sua implementação.

8. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> chama sua implementação para abrir o arquivo e inicializar o objeto do projeto, por exemplo, Project1.

9. O ambiente `IVsProjectUpgrade::UpgradeProject` chama sua implementação para determinar se o arquivo do projeto precisa ser atualizado.

10. Você <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> liga e passa <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> um `rgfQueryEdit` valor para o parâmetro.

11. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> `VSQueryEditResult` retorna <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> para e `VSQueryEditResultFlags`a broca é definida em .

12. Suas <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> chamadas `IVsQueryEditQuerySave::QueryEditFiles` <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>de <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>implementação ( , ).

Esta chamada pode fazer com que uma nova cópia do arquivo do projeto seja verificada e a versão mais recente recuperada, bem como a necessidade de recarregar seu arquivo de projeto. Neste ponto, uma das duas coisas acontecem:

- Se você lidar com a recarga do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> seu próprio projeto, então o ambiente chama sua implementação (VSITEMID_ROOT). Quando receber essa chamada, recarregue a primeira instância do seu projeto (Project1) e continue atualizando seu arquivo de projeto. O ambiente sabe que você lida com `true` a <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>recarga do seu próprio projeto se você voltar para ( ).

- Se você não lidar com a recarga `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> do<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>seu próprio projeto, então você retorna para ( ). Nesse caso, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>antes do retorno (QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits), o ambiente cria outra nova instância do seu projeto, por exemplo, o Project2, da seguinte forma:

    1. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> solicita seu primeiro objeto de projeto, O Projeto1, colocando assim esse objeto no estado inativo.

    2. O ambiente `IVsProjectFactory::CreateProject` chama sua implementação para criar uma segunda instância do seu projeto, o Project2.

    3. O ambiente `IPersistFileFormat::Load` chama sua implementação para abrir o arquivo e inicializar o segundo objeto do projeto, Project2.

    4. O ambiente `IVsProjectUpgrade::UpgradeProject` exige uma segunda vez para determinar se o objeto do projeto deve ser atualizado. No entanto, essa chamada é feita em uma nova, segunda instância do projeto, O Projeto2. Este é o projeto que é aberto na solução.

        > [!NOTE]
        > No caso de seu primeiro projeto, Project1, ser colocado no <xref:Microsoft.VisualStudio.VSConstants.S_OK> estado inativo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> então você deve retornar da primeira chamada para sua implementação.

    5. Você <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> liga e passa <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> um `rgfQueryEdit` valor para o parâmetro.

    6. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK> retorna e a atualização pode prosseguir porque o arquivo do projeto pode ser escrito.

Se você não conseguir <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> `IVsProjectUpgrade::UpgradeProject`atualizar, retorne de . Se nenhum upgrade for necessário ou você `IVsProjectUpgrade::UpgradeProject` optar por não atualizar, trate a chamada como uma opção. Se você <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>retornar, um nó de espaço reservado é adicionado à solução para o seu projeto.

## <a name="upgrading-project-items"></a>Atualizando Itens de Projeto

Se você adicionar ou gerenciar itens dentro de sistemas de projeto que você não implementar, você pode precisar participar do processo de atualização do projeto. Crystal Reports é um exemplo de um item que pode ser adicionado ao sistema do projeto.

Normalmente, os implementadores de itens do projeto querem aproveitar um projeto já totalmente instanciado e atualizado, pois precisam saber quais são as referências do projeto e quais outras propriedades do projeto estão lá para tomar uma decisão de upgrade.

### <a name="to-get-the-project-upgrade-notification"></a>Para obter a notificação de atualização do projeto

1. Defina <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> o sinalizador (definido em vsshell80.idl) na implementação do item do projeto. Isso faz com que o item do projeto VSPackage seja carregado automaticamente quando o shell do Visual Studio determina que um sistema de projeto está em processo de atualização.

2. Informe <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> interface através do método.

3. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interface é acionada depois que a implementação do sistema de projeto tiver concluído suas operações de atualização e o novo projeto atualizado for criado. Dependendo do cenário, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>é <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>acionada após <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> os métodos.

### <a name="to-upgrade-the-project-item-files"></a>Para atualizar os arquivos de itens do projeto

1. Você deve gerenciar cuidadosamente o processo de backup de arquivos na implementação do item do projeto. Isso se aplica, em particular, a um `fUpgradeFlag` backup lado <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> a lado, <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>onde o parâmetro do método é definido para , onde os arquivos que haviam sido copiados são colocados junto com arquivos designados como ".old". Os arquivos com backup mais antigos do tempo do sistema quando o projeto foi atualizado podem ser designados como obsoletos. Além disso, eles podem ser substituídos a menos que você tome medidas específicas para evitar isso.

2. No momento em que o item do projeto recebe uma notificação da atualização do projeto, o **Visual Studio Conversion Wizard** ainda é exibido. Portanto, você deve usar os <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> métodos da interface para fornecer mensagens de atualização para a interface do assistente.

## <a name="see-also"></a>Confira também

- [Projetos](../../extensibility/internals/projects.md)
