---
title: Disponibilizando comandos | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707330"
---
# <a name="making-commands-available"></a>Disponibilizando comandos

Quando vários VSPackages são adicionados ao Visual Studio, a interface do usuário (UI) pode ficar superlotada com comandos. Você pode programar seu pacote para ajudar a reduzir esse problema, da seguinte forma:

- Programe o pacote para que ele seja carregado somente quando um usuário o exigir.

- Programe o pacote para que seus comandos sejam exibidos somente quando forem exigidos no contexto do estado atual do ambiente de desenvolvimento integrado (IDE).

## <a name="delayed-loading"></a>Carregamento atrasado

A maneira típica de habilitar o carregamento atrasado é projetar o VSPackage para que seus comandos sejam exibidos na ui, mas o pacote em si não é carregado até que um usuário clique em um dos comandos. Para conseguir isso, no arquivo .vsct, crie comandos que não tenham bandeiras de comando.

O exemplo a seguir mostra a definição de um comando de menu a partir de um arquivo .vsct. Este é o comando gerado pelo Modelo de Pacote do Visual Studio quando a opção **Comando de Menu** no modelo é selecionada.

```xml
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <Strings>
    <CommandName>cmdidTestCommand</CommandName>
    <ButtonText>Test Command</ButtonText>
  </Strings>
</Button>
```

No exemplo, se o `MyMenuGroup`grupo pai, é filho de um menu de nível superior, como o menu **Ferramentas,** o comando ficará visível nesse menu, mas o pacote que executa o comando não será carregado até que o comando seja clicado por um usuário. No entanto, ao programar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o comando para implementar a interface, você pode habilitar o pacote a ser carregado quando o menu que contém o comando for expandido pela primeira vez.

Observe que o carregamento atrasado também pode melhorar o desempenho de inicialinicial.

## <a name="current-context-and-the-visibility-of-commands"></a>Contexto atual e a visibilidade dos comandos

Você pode programar comandos VSPackage para serem visíveis ou ocultos, dependendo do estado atual dos dados do VSPackage ou das ações que são relevantes no momento. Você pode habilitar o VSPackage para definir o estado de seus <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> comandos, normalmente usando uma implementação do método a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> partir da interface, mas isso requer que o VSPackage seja carregado antes que ele possa executar o código. Em vez disso, recomendamos que você habilite o IDE para gerenciar a visibilidade dos comandos sem carregar o pacote. Para fazer isso, no arquivo .vsct, associe comandos a um ou mais contextos especiais de interface do usuário. Esses contextos de Interface do Usão são identificados por um GUID conhecido como *guid de contexto de comando*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]monitora alterações resultantes de ações do usuário, como carregar um projeto ou ir da edição para a construção. À medida que as alterações ocorrem, o aparecimento do IDE é automaticamente modificado. A tabela a seguir mostra quatro contextos principais de alteração do IDE que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitora.

| Tipo de Contexto | Descrição |
|-------------------------| - |
| Tipo de projeto ativo | Para a maioria `GUID` dos tipos de projeto, esse valor é o mesmo que o GUID do VSPackage que implementa o projeto. No [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] entanto, os `GUID` projetos usam o Tipo de Projeto como valor. |
| Janela ativa | Normalmente, esta é a última janela de documento ativo que estabelece o contexto atual da interface do iu para vinculações de chaves. No entanto, também pode ser uma janela de ferramenta que tem uma tabela de vinculação chave que se assemelha ao navegador interno da Web. Para janelas de documentos com várias guias, como o `GUID`editor HTML, cada guia tem um contexto de comando diferente . |
| Serviço de idioma ativo | O serviço de idiomas associado ao arquivo que atualmente é exibido em um editor de texto. |
| Janela da ferramenta ativa | Uma janela de ferramenta que está aberta e tem foco. |

Uma quinta grande área de contexto é o estado de Interface do IDE. Os contextos de Interface do `GUID`EI são identificados por contextos de comando ativos, da seguinte forma:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>

Esses GUIDs são marcados como ativos ou inativos, dependendo do estado atual do IDE. Vários contextos de interface do reino do reino eletrônico podem estar ativos ao mesmo tempo.

### <a name="hide-and-display-commands-based-on-context"></a>Ocultar e exibir comandos com base no contexto

Você pode exibir ou ocultar um comando de pacote no IDE sem carregar o pacote em si. Para isso, defina o comando no arquivo .vsct `DefaultDisabled` `DefaultInvisible`do `DynamicVisibility` pacote usando os sinalizadores de comando e adicionando um ou mais elementos [VisibilityItem](../../extensibility/visibilityitem-element.md) à seção [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) Quando um contexto `GUID` de comando especificado se torna ativo, o comando é exibido sem carregar o pacote.

### <a name="custom-context-guids"></a>GUIDs de contexto personalizado

Se um guid de contexto de comando apropriado ainda não estiver definido, você pode definir um em seu VSPackage e, em seguida, programá-lo para ser ativo ou inativo, conforme necessário para controlar a visibilidade de seus comandos. Use <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> o serviço para:

- Registre GUIDs de contexto <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (chamando o método).

- Obtenha o estado `GUID` de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> contexto (chamando o método).

- Ligue `GUID`e desligue o contexto <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (chamando o método).

    > [!CAUTION]
    > Certifique-se de que o vsPackage não afete o estado de qualquer GUID de contexto existente, pois outros VSPackages podem depender deles.

## <a name="example"></a>Exemplo

O exemplo a seguir de um comando VSPackage demonstra a visibilidade dinâmica de um comando que é gerenciado por contextos de comando sem carregar o VSPackage.

O comando é definido para ser ativado e exibido sempre que uma solução existir; ou seja, sempre que um dos seguintes GUIDs de contexto de comando estiver ativo:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

No exemplo, observe que cada sinalizador de comando é um elemento de [bandeira de comando](../../extensibility/command-flag-element.md) separado.

```xml
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"
        priority="0x0100" type="Button">
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />
  <Icon guid="guidImages" id="bmpPic1" />
  <CommandFlag>DefaultDisabled</CommandFlag>
  <CommandFlag>DefaultInvisible</CommandFlag>
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <CommandName>cmdidMyCommand</CommandName>
    <ButtonText>My Command name</ButtonText>
  </Strings>
</Button>
```

Observe também que cada contexto de Interface `VisibilityItem` do UI deve ser dado em um elemento separado, da seguinte forma.

```xml
<VisibilityConstraints>
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />
</VisibilityConstraints>
```

## <a name="see-also"></a>Confira também

- [Adicione um comando à barra de ferramentas do Solution Explorer](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Roteamento de comando em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)
- [Adicionar itens de menu dinamicamente](../../extensibility/dynamically-adding-menu-items.md)
