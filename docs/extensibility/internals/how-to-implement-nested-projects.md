---
title: 'Como: Implementar Projetos Aninhados | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707978"
---
# <a name="how-to-implement-nested-projects"></a>Como: Implementar projetos aninhados

Quando você cria um tipo de projeto aninhado, existem várias etapas adicionais que devem ser implementadas. Um projeto pai assume algumas das mesmas responsabilidades que a solução tem para seus projetos aninhados (crianças). O projeto pai é um contêiner de projetos semelhantes a uma solução. Em particular, há vários eventos que devem ser levantados pela solução e pelos projetos-mãe para construir a hierarquia de projetos aninhados. Esses eventos são descritos no processo seguinte para a criação de projetos aninhados.

## <a name="create-nested-projects"></a>Criar projetos aninhados

1. O ambiente de desenvolvimento integrado (IDE) carrega as informações de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> arquivo de projeto e inicialização do projeto pai ligando para a interface. O projeto pai é criado e adicionado à solução.

    > [!NOTE]
    > Neste ponto, é muito cedo para o projeto pai criar o projeto aninhado porque o projeto pai deve ser criado antes que os projetos infantis possam ser criados. Após essa sequência, o projeto pai pode aplicar configurações aos projetos dos filhos e os projetos infantis podem obter informações dos projetos dos pais, se necessário. Esta seqüência é se for necessária por clientes como controle de código fonte (SCC) e **Solution Explorer**.

     O projeto pai deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> aguardar que o método seja chamado pelo IDE antes que ele possa criar seu projeto aninhado (filho) ou projetos.

2. O IDE `QueryInterface` solicita o <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>projeto pai para . Se essa chamada for bem-sucedida, o IDE chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> método do pai para abrir todos os projetos aninhados para o projeto pai.

3. O projeto pai <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> chama o método para notificar os ouvintes de que projetos aninhados estão prestes a ser criados. A SCC, por exemplo, está ouvindo esses eventos para saber se as etapas do processo de solução e criação de projetos estão ocorrendo em ordem. Se as etapas ocorrerem fora de ordem, a solução pode não estar registrada com o controle do código-fonte corretamente.

4. O projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> pai chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> o método ou o método em cada um de seus projetos infantis.

     Você <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> passa `AddVirtualProject` para o método para indicar que o projeto virtual (aninhado) deve ser adicionado à janela do projeto, excluído da compilação, adicionado ao controle de código fonte, e assim por diante. `VSADDVPFLAGS`permite controlar a visibilidade do projeto aninhado e indicar qual funcionalidade está associada a ele.

     Se você recarregar um projeto filho anteriormente existente que tenha um GUID de projeto `AddVirtualProjectEx`armazenado no arquivo de projeto do projeto pai, o projeto pai será chamados . A única `AddVirtualProject` diferença `AddVirtualProjectEX` entre `AddVirtualProjectEX` e é que tem um parâmetro para `guidProjectID` permitir que o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> projeto pai especifique uma instância por instância para o projeto filho para habilitar e funcionar corretamente.

     Se não houver GUID disponível, como quando você adiciona um novo projeto aninhado, a solução cria um para o projeto no momento em que ele é adicionado ao pai. É responsabilidade do projeto pai persistir esse projeto GUID em seu arquivo de projeto. Se você excluir um projeto aninhado, o GUID para esse projeto também pode ser excluído.

5. O IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> chama o método em cada projeto filho do projeto pai.

     O projeto pai `IVsParentProject` deve ser implementado se você quiser fazer ninhos de projetos. Mas o projeto `QueryInterface` pai `IVsParentProject` nunca exige, mesmo que tenha projetos-mãe por baixo. A solução lida com `IVsParentProject` a chamada e, `OpenChildren` se for implementada, chama para criar os projetos aninhados. `AddVirtualProjectEX`é sempre `OpenChildren`chamado de . Ele nunca deve ser chamado pelo projeto pai para manter os eventos de criação da hierarquia em ordem.

6. O IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> chama o método do projeto infantil.

7. O projeto pai <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> chama o método para notificar os ouvintes de que os projetos de crianças para os pais foram criados.

8. O IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> chama o método no projeto pai depois que todos os projetos infantis foram abertos.

     Se ele ainda não existir, o projeto pai cria um `CoCreateGuid`GUID para cada projeto aninhado, chamando .

    > [!NOTE]
    > `CoCreateGuid`é uma API COM chamada quando um GUID deve ser criado. Para obter mais `CoCreateGuid` informações, consulte e GUIDs na Biblioteca MSDN.

     O projeto-mãe armazena este GUID em seu arquivo de projeto a ser recuperado na próxima vez que ele for aberto no IDE. Consulte o passo 4 para obter `AddVirtualProjectEX` mais informações `guidProjectID` relacionadas à chamada de para recuperar o projeto para a criança.

9. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> método é então chamado para o ItemID pai que, por convenção, você delega ao projeto aninhado. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera as propriedades do nó que aninha um projeto que você deseja delegar quando é chamado pelo pai.

     Como os projetos de pais e filhos são programados de forma instanciada, você pode definir propriedades para projetos aninhados neste momento.

    > [!NOTE]
    > Você não só recebe as informações de contexto do projeto aninhado, mas também pode perguntar se o projeto pai tem algum contexto para esse item, verificando [__VSHPROPID. VSHPROPID_UserContext.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>) Dessa forma, você pode adicionar atributos de ajuda dinâmicos extras e opções de menu específicas para projetos individuais aninhados.

10. A hierarquia é construída para exibição no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> Solution **Explorer** com uma chamada para o método.

     Você passa a hierarquia para `GetNestedHierarchy` o ambiente para construir a hierarquia para exibição no Solution Explorer. Dessa forma, a solução sabe que o projeto existe e pode ser gerenciado para construção pelo gerenciador de compilação, ou pode permitir que arquivos no projeto sejam colocados sob controle de código fonte.

11. Quando todos os projetos aninhados para o Projeto1 foram criados, o controle é repassado de volta para a solução e o processo é repetido para o Projeto2.

     Esse mesmo processo de criação de projetos aninhados ocorre para um projeto infantil que tem um filho. Neste caso, se o BuildProject1, que é filho do Project1, tivesse projetos infantis, eles seriam criados após o BuildProject1 e antes do Project2. O processo é recursivo e a hierarquia é construída de cima para baixo.

     Quando um projeto aninhado é fechado porque o usuário fechou a `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>solução ou o projeto específico em si, o outro método em , é chamado. O projeto pai envolve <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> chamadas para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> método com o método e os métodos para notificar os ouvintes para eventos de solução que os projetos aninhados estão sendo fechados.

Os seguintes tópicos tratam de vários outros conceitos a serem considerados quando você implementa projetos aninhados:

- [Considerações para descarregar e recarregar projetos aninhados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Suporte do Assistente para projetos aninhados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementar o manuseio de comandos para projetos aninhados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrar a caixa de diálogo AddItem para projetos aninhados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Confira também

- [Adicionar itens à caixa de diálogo Adicionar novo item](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registre modelos de projetos e itens](../../extensibility/internals/registering-project-and-item-templates.md)
- [Checklist: Crie novos tipos de projetos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)
- [Arquivo Assistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
