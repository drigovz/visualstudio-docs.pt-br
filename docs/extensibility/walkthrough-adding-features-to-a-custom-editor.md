---
title: 'Passo a passo: Adicionando recursos a um editor personalizado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65ef0edf76780ba7c8b6f5d9347195c286bec466
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649839"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Passo a passo: Adicione recursos a um editor personalizado
Depois de criar um editor personalizado, você pode adicionar mais recursos a ele.

## <a name="to-create-an-editor-for-a-vspackage"></a>Para criar um editor para um VSPackage

1. Crie um editor personalizado usando o modelo de projeto Visual Studio Package.

     Para obter mais informações, consulte [Passo a Passo: Crie um editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Decida se deseja que seu editor suporte uma única visualização ou vários pontos de vista.

     Um editor que suporta o comando **Nova janela,** ou tem exibição de formulário e exibição de código, requer objetos de dados de documentos separados e objetos de exibição de documentos. Em um editor que suporta apenas uma única visualização, o objeto de dados do documento e o objeto de exibição de documento podem ser implementados no mesmo objeto.

     Para um exemplo de vários visualizações, consulte ['Suportar exibições de vários documentos'.](../extensibility/supporting-multiple-document-views.md)

3. Implemente uma fábrica de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> editores configurando a interface.

     Para obter mais informações, consulte [As fábricas do Editor](/visualstudio/extensibility/editor-factories?view=vs-2015).

4. Decida se deseja que seu editor use ativação no local ou incorporação simplificada para gerenciar a janela de objeto de exibição de documento.

     Uma janela de editor de incorporação simplificada hospeda uma exibição padrão de documento, enquanto uma janela do editor de ativação no local hospeda um controle ActiveX ou outro objeto ativo como exibição de documento. Para obter mais informações, consulte [Incorporação Simplificada](../extensibility/simplified-embedding.md) e [ativação no local](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> a interface para lidar com comandos.

6. Fornecer persistência e resposta do documento às alterações externas do arquivo:

    1. Para persistir o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arquivo, implemente e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> no objeto de dados do documento do seu editor.

    2. Para responder a alterações <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> externas de arquivos, implemente e no objeto de dados do documento do seu editor.

        > [!NOTE]
        > Chame `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> para obter um `IVsFileChangeEx`ponteiro para .

7. Coordenar eventos de edição de documentos com controle de código fonte. Siga estas etapas:

    1. Obtenha um `IVsQueryEditQuerySave2` ponteiro `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>chamar .

    2. Quando o primeiro evento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> edição ocorrer, chame o método.

         Este método solicita ao usuário que verifique o arquivo se ele ainda não foi verificado. Certifique-se de lidar com uma condição de "arquivo não verificado" para evitar erros.

    3. Da mesma forma, antes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> salvar o arquivo, chame o método.

         Este método solicita ao usuário que salve o arquivo se ele não foi salvo ou se ele mudou desde a última salvação.

8. Habilite a janela **Propriedades** para exibir propriedades para texto selecionado no editor. Siga estas etapas:

    1. Ligue <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> cada vez que a seleção de texto muda, passando em sua implementação de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.

    2. Chame `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> o serviço para <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>obter um ponteiro para .

9. Permitir que os usuários arrastem e soltem itens entre o editor e a **Caixa de Ferramentas,** ou entre editores externos (como o Microsoft Word) e a **Caixa de Ferramentas**. Siga estas etapas:

    1. Implemente `IDropTarget` em seu editor para alertar o IDE de que seu editor é um alvo de queda.

    2. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> a interface na visualização para que seu editor possa ativar e desativar itens na **Caixa de ferramentas**.

    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> Implemente `QueryService` e <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> convoque o <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> serviço <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> para obter um ponteiro para as interfaces e interfaces.

         Essas etapas permitem que o VSPackage adicione novos itens à **caixa de ferramentas**.

10. Decida se deseja outros recursos opcionais para o seu editor.

    - Se você quiser que seu editor suporte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>a encontrar e substituir comandos, implemente .

    - Se você quiser usar uma janela de ferramenta `IVsDocOutlineProvider`de contorno de documento em seu editor, implemente .

    - Se você quiser usar uma barra de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> status `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> em seu editor, implemente e peça para obter um ponteiro para `IVsStatusBar`.

         Por exemplo, um editor pode exibir informações de linha/coluna, modo de seleção (fluxo/caixa) e modo de inserção (inserir/ overstrike).

    - Se você quiser que `Undo` seu editor suporte o comando, o método recomendado é usar o modelo de gerenciador de desfazer OLE. Como alternativa, você pode fazer `Undo` com que o editor manuseie o comando diretamente.

11. Crie informações de registro, incluindo os GUIDs para o VSPackage, os menus, o editor e outros recursos.

     A seguir, um exemplo genérico de código que você colocaria em seu script de arquivo *.rgs* para demonstrar como registrar corretamente um editor.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Implemente suporte de ajuda sensível ao contexto.

     Esta etapa permite que você forneça suporte à janela F1 Help and Dynamic Help para itens do seu editor. Para obter mais informações, consulte [Como: Fornecer contexto para editores](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015).

13. Exponha um modelo de objeto de `IDispatch` automação do seu editor implementando a interface.

     Para obter mais informações, consulte [Contribuindo para o Modelo de Automação](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programação robusta

- A instância do editor é criada <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> quando o IDE chama o método. Se o editor suportar `CreateEditorInstance` várias visualizações, criará os dados do documento e os objetos de exibição do documento. Se o objeto de dados do documento `punkDocDataExisting` já estiver `IVsEditorFactory::CreateEditorInstance`aberto, um valor não nulo será passado para . A implementação da fábrica do editor deve determinar se um objeto de dados de documento existente é compatível consultando interfaces apropriadas nele. Para obter mais informações, consulte [Como suporte a várias exibições de documentos](../extensibility/supporting-multiple-document-views.md).

- Se você usar a abordagem de <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> incorporação simplificada, implemente a interface.

- Se você decidir usar a ativação no local, implemente as seguintes interfaces:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > A `IOleInPlaceComponent` interface é usada para evitar a fusão do menu OLE 2.

   Sua `IOleCommandTarget` implementação lida com comandos como **Corte,** **Cópia**e **Colar**. Ao `IOleCommandTarget`implementar, decida se o seu editor requer seu próprio arquivo *.vsct* para definir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sua própria estrutura de menu de comando ou se ele pode implementar comandos padrão definidos por . Normalmente, os editores usam e estendem os menus do IDE e definem suas próprias barras de ferramentas. No entanto, muitas vezes é necessário que um editor defina seus próprios comandos específicos, além de usar o conjunto de comandos padrão do IDE. Seu editor deve declarar os comandos padrão que usa e, em seguida, definir quaisquer novos comandos, menus de contexto, menus de nível superior e barras de ferramentas em um arquivo *.vsct.* Se você criar um editor de <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> ativação no local, implemente e defina os menus e barras de ferramentas para o editor em um arquivo *.vsct* em vez de usar a fusão do menu OLE 2.

- Para evitar a aglomeração de comandos de menu na ui, você deve usar os comandos existentes no IDE antes de inventar novos comandos. Os comandos compartilhados são definidos em *SharedCmdDef.vsct* e *ShellCmdDef.vsct*. Esses arquivos são instalados por padrão no subdiretório VisualStudioIntegration\Common\Inc de sua [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] instalação.

- `ISelectionContainer`pode expressar seleções únicas e múltiplas. Cada objeto selecionado é `IDispatch` implementado como um objeto.

- O IDE `IOleUndoManager` implementa como um <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> serviço acessível a partir de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>um ou como um objeto que pode ser instanciado através de . Seu editor implementa `IOleUndoUnit` a `Undo` interface para cada ação.

- Há dois lugares que um editor personalizado pode expor objetos de automação:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Confira também

- [Contribua para o modelo de automação](../extensibility/internals/contributing-to-the-automation-model.md)
